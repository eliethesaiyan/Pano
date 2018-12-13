# Pano

## Guidance to run the code

1. follow the instruction on how to  download [coco](http://cocodataset.org/#download) panoptic dataset and store in the root folder as coco/
following this tree structure
```bash
coco
├── annotations
├── converted_data
├── __MACOSX
├── panoptic_annotations_trainval2017.zip
├── test2017
├── train2017
└── val2017
```
2. Follow the instruction and install [CocoApi](https://github.com/cocodataset/cocoapi)


3. in the root folder type the following command to generate change panoptic format to detection for trainval/val2017
```
python2 scripts/panoptic2detection_coco_format.py   --input_json_file coco/annotations/panoptic_train2017.json \
--output_json_file coco/converted_data/panoptic_coco_detection_train2017.json \ 
 --segmentations_folder coco/annotations/panoptic_train2017/ --categories_json_file panopticapi/panoptic_coco_categories.json
```

Repeat the same for segmentation format change

```
python2 scripts/panoptic2segmentation_coco_format.py   --input_json_file coco/annotations/panoptic_train2017.json \
--output_json_file coco/converted_data/panoptic_segmentation_train2017.json \  
 --segmentations_folder coco/annotations/panoptic_train2017/ --categories_json_file panopticapi/panoptic_coco_categories.json
```


4. Install requirements for Mask-RCNN

`pip install -r requirement.txt`

5. run the following command to start training

`PYTHONPATH=./ python samples/coco/coco2017.py train  --dataset=coco/ --model=imagenet # Python3

