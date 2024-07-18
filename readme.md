### Traning
Có bao gồm 3 file .ipynb để finetune DETR, yolov9, đánh giá mô hình và các file phụ trợ

Để thực hiện finetune yolov9, DETR chạy file Kaggle với đường dẫn và data phù hợp:
Với YOLOv9 có dạng:
```
path/to/
    train/          # train folder
        images/     # images folder
        labels/     # lables fodler (.txt file)
    valid/          # valid folder
        images/
        labels/
    test/images     # test folder
        images/
        labels/
    data.yaml       # data_path_config
```
Với DETR có dạng:
```
path/to/
    train/                      # train folder
        image1.jpg ...          # train images
        _annotations.coco.json  # train annotation
    valid/
        image2.jpg ...          # valid images
        _annotations.coco.json  # valid annotation
    test/
        image3.jpg ...          # test images
        _annotations.coco.json  # test annotation
```

### Evaluate
Để đánh giá các mô hình, chạy file SummarizeML.ipynb
Một số lưu ý:
+ Thay thế file val_dual.py, val.py ở trong thư mục yolov9 clone về bằng các file trong thư mục evaluate_utils
+ Thay thế "data_path" ở dòng 42 của file val.py và dòng 43 của val_dual.py bằng đường dẫn đến _annotations.coco.json của thư mục test của DETR data
+ Thay thế "anno_json" ở dòng 295 của file val.py và dòng 298 của val_dual.py bằng đường dẫn đến _annotations.coco.json của thư mục test của DETR data
+ Thay thế SummarizeML.ipynb trong các đường dẫn cho phù hợp
+ Với file /yolov9/utils/general/py:
    Đánh giá mô hình *GELAN-c* thì dòng 903 là "prediction = prediction[0]"
    Đánh giá mô hình *YOLOv9-c* thì dòng 903 là "prediction = prediction[0][1]"