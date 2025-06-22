# fruits_bbox
What is Object Detection?
Object detection is a computer vision technique used to locate and classify objects within an image. Unlike image classification (which only tells you what’s in an image), object detection also tells you where the object is using bounding boxes.

Each bounding box is defined by four coordinates:

Top-left corner: xtl, ytl

Bottom-right corner: xbr, ybr

This allows models like YOLO, SSD, or Faster R-CNN to not only recognize objects but also pinpoint their exact location in the image.

Why Padding Was Needed
In my dataset, each image had different dimensions. However, most object detection models expect images of the same size (e.g., 480×480). Simply resizing the images would distort the objects and bounding boxes.

To solve this, I used a technique called aspect-ratio preserving padding (letterbox padding):

Scaling: I scaled each image so that its longer side fits exactly into a 480×480 square.

Padding: I then padded the shorter side with equal margins (top-bottom or left-right) to fill up the square without stretching the image.

Bounding Box Update: After resizing and padding, I adjusted the bounding box coordinates so they remained accurate in the new image dimensions.

This method ensures:

- The object shape remains unchanged.
- The bounding boxes still match the object positions.
- All images are uniform in size, ready for training.