# VidSTG-Dataset
This repository provides the dataset introduced by the paper "Where Does It Exist: Spatio-Temporal Video Grounding for Multi-Form Sentences".


### Introduction
The VidSTG dataset is constructed based on video relation dataset [VidOR](https://xdshang.github.io/docs/vidor.html). VidOR contains 7,000, 835 and 2,165 videos for training, validation and testing, respectively. Since box annotations of testing videos are unavailable yet, we omit testing videos, split 10\% training videos as our validation data and regard original validation videos as the testing data. The concrete annotation process can be found in our paper "Where Does It Exist: Spatio-Temporal Video Grounding for Multi-Form Sentences".

### Data 
The original VidOR dataset contains the raw videos and dense bounding box annotations for each <subject, predicate, object> triplet. These data can be downloaded from [the official website](https://xdshang.github.io/docs/vidor.html).

We only privide the video partition files and sentence annotation files here. The [train_files.json](https://github.com/Guaranteer/VidSTG-Dataset/blob/master/annotations/train_files.json), [val_files.json](https://github.com/Guaranteer/VidSTG-Dataset/blob/master/annotations/val_files.json) and [test_files.json](https://github.com/Guaranteer/VidSTG-Dataset/blob/master/annotations/test_files.json) contain the video ids in the training, validation and testing sets. And [train_annotations.json](https://github.com/Guaranteer/VidSTG-Dataset/blob/master/annotations/train_annotations.json), [val_annotations.json](https://github.com/Guaranteer/VidSTG-Dataset/blob/master/annotations/val_annotations.json) and [test_annotations.json](https://github.com/Guaranteer/VidSTG-Dataset/blob/master/annotations/test_annotations.json) contain the sentence annotations.

### Annotation Structure
Each annotation is organized by

    {
    "vid": "5159741010",                            # Video ID
    "frame_count": 219,                             # Number of frames
    "fps": 29.97002997002997, 
    "width": 1920, 
    "height": 1080, 
    "subject/objects": [                            # List of subject/objects
        {
            "tid": 0,                               # Subject/object ID
            "category": "bicycle"
        }, 
        ...
    ], 
    "used_segment":                                 # Input segment 
    {
        "begin_fid": 0,                             # Begin frame ID
        "end_fid": 210                              # End frame ID
    }, 
    "used_relation":                                # Annotated relation
    {
        "subject_tid": 0,                           # Subject ID
        "object_tid": 1,                            # Object ID 
        "predicate": "in_front_of", 
        "begin_fid": 13,                            # Begin frame ID
        "end_fid": 45                               # End frame ID
    }, 
    "temporal_gt":                                  # Temporal ground truth
    {
        "begin_fid": 13,                            # Begin frame ID
        "end_fid": 45                               # End frame ID
    }, 
    "captions":                                     # Declarative sentences
    [
        {
        "description": "there is a red ...",        
        "type": person,                              
        "target_id": 1,                             # Target ID of the queried object
        }
    ],
    "questions":                                    # Interrogative sentences
    [
        {
        "description": "there is a red ...",        
        "type": object,                              
        "target_id": 0,                             # Target ID of the queried object
        }, 
        ...
    ]
    }


### Citing Our Paper

If you find this dataset useful in your research, please consider citing:

    @inproceedings{zhang2020does,
        title={Where Does It Exist: Spatio-Temporal Video Grounding for Multi-Form Sentences},
        author={Zhang, Zhu and Zhao, Zhou and Zhao, Yang and Wang, Qi and Liu, Huasheng and Gao, Lianli},
        booktitle={CVPR},
        year={2020}
    }


