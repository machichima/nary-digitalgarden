---
{"dg-publish":true,"dg-path":"ML/Pytorch/","permalink":"//"}
---


[[Learn/ML/Pytorch/Pytorch\|Pytorch]]
**Tags**:: 
**Links**:: [tutorial](https://pytorch.org/tutorials/intermediate/tensorboard_tutorial.html) - [my colab](https://colab.research.google.com/drive/15HcA8Wqw9gXGTYQZ9qPxjyEIFiyosD5q?usp=sharing)
**Canvas**:: 

> if showing 403 when launching tensorboard in colab, enable all cookies from colab

## install
```command
pip install tensorboard
```

## Usage

### set up
- add `%` before commands if using Jupyter Notebook

```command
load_ext tensorboard
```
- command to load tensorboard

```python
from torch.utils.tensorboard import SummaryWriter

# default `log_dir` is "runs" - we'll be more specific here
writer = SummaryWriter('{log_dir}/fashion_mnist_experiment_1')
```
- set up the object and the log_dir for tensorboard
- `{log_dir}` is `runs` in the tutorial

```command
tensorboard --logdir={log_dir}
```
- launch tensorboard

### Show images

- open "IMAGES" section in TensorBoard to see the figure

```python
# create grid of images
img_grid = torchvision.utils.make_grid(imgs)

# write to tensorboard
writer.add_image('title', img_grid)
```

### Inspect the model
- open "GRAPHS" section in TensorBoard to see the figure

```python
writer.add_graph(net, inputs)
writer.close()
```
- net: your network's name
- inputs: the inputs to model

### Adding Projector to TensorBoard
> projects data points in lower dimentional to visualize

- open "PROJECTOR" section in TensorBoard to see the figure

```python
writer.add_embedding(features,
          metadata=class_labels,
          label_img=images.unsqueeze(1))
writer.close()
```
- label_img: 資料點要顯示的圖片
- features: 座標點 (會將圖片拉平)

### Tracking model training with TensorBoard
> use `writer.add_figure()` to add a line figure to show the loss

- below are the full code from tutorial
- open "SCALARS" section in TensorBoard to see the figure

- help functions
```python
def images_to_probs(net, images):
  '''
  Generates predictions and corresponding probabilities from a trained
  network and a list of images
  '''
  output = net(images)
  # convert output probabilities to predicted class
  _, preds_tensor = torch.max(output, 1)
  preds = np.squeeze(preds_tensor.cpu().numpy())
  return preds, [F.softmax(el, dim=0)[i].item() for i, el in zip(preds, output)]

def plot_classes_preds(net, images, labels):
    '''
    Generates matplotlib Figure using a trained network, along with images
    and labels from a batch, that shows the network's top prediction along
    with its probability, alongside the actual label, coloring this
    information based on whether the prediction was correct or not.
    Uses the "images_to_probs" function.
    '''
    preds, probs = images_to_probs(net, images)
    # plot the images in the batch, along with predicted and true labels
    fig = plt.figure(figsize=(12, 48))
    for idx in np.arange(4):
      ax = fig.add_subplot(1, 4, idx+1, xticks=[], yticks=[])
      matplotlib_imshow(images[idx], one_channel=True)
      ax.set_title("{0}, {1:.1f}%\n(label: {2})".format(
        classes[preds[idx]],
        probs[idx] * 100.0,
        classes[labels[idx]]),
        color=("green" if preds[idx]==labels[idx].item() else "red"))
    return fig

```

- training loop
```python
running_loss = 0.0
for epoch in range(1):
  for i, data in enumerate(trainloader, 0):
    inputs, labels = data
    optimizer.zero_grad()
    outputs = net(inputs.to('cuda'))
    loss = loss_fn(outputs.to('cuda'), labels.to('cuda'))
    loss.backward()
    optimizer.step()

    if i % 1000 == 999:    # every 1000 mini-batches...

      # ...log the running loss
      writer.add_scalar('training loss',
                running_loss / 1000,
                epoch * len(trainloader) + i)

      # ...log a Matplotlib Figure showing the model's predictions on a
      # random mini-batch
      writer.add_figure('predictions vs. actuals',
                plot_classes_preds(net, inputs.to('cuda'), labels.to('cuda')),
                global_step=epoch * len(trainloader) + i)
      running_loss = 0.0

print('Finished Training') 
```

### Show PR curve in TensorBoard
> show precision - recall cureve

- below are the full code from tutorial
- open "PR CURVE" section in TensorBoard to see the figure

```python
# 1. gets the probability predictions in a test_size x num_classes Tensor
# 2. gets the preds in a test_size Tensor
# takes ~10 seconds to run
class_probs = []
class_label = []
with torch.no_grad():
  for data in testloader:
    images, labels = data
    output = net(images.to('cuda'))
    class_probs_batch = [F.softmax(el, dim=0) for el in output.to('cuda')]

    class_probs.append(class_probs_batch)
    class_label.append(labels.to('cuda'))

test_probs = torch.cat([torch.stack(batch) for batch in class_probs])
test_label = torch.cat(class_label)

# helper function
def add_pr_curve_tensorboard(class_index, test_probs, test_label, global_step=0):
  '''
  Takes in a "class_index" from 0 to 9 and plots the corresponding
  precision-recall curve
  '''
  tensorboard_truth = test_label == class_index
  tensorboard_probs = test_probs[:, class_index]

  writer.add_pr_curve(classes[class_index],
              tensorboard_truth,
              tensorboard_probs,
              global_step=global_step)
  writer.close()

# plot all the pr curves
for i in range(len(classes)):
  add_pr_curve_tensorboard(i, test_probs, test_label)
```

