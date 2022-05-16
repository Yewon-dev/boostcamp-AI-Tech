# Segmentation Models - Library

## SMP (segmentation models pytorch)

- 9 models architectures for binary and multi class segmentation (including legendary Unet)
- 104 available encoders (timm 사용가능)
- All encoders have pre-trained weights for faster ans better convergence



### Library 설치

``` bash
pip install https://github.com/qubvel/segmentation_models.pytorch
```



### Library Import

```python
import segmentation_models_pytorch as smp
```



### 모델 불러오기

```python
model = smp.Unet(
		encoder_name="efficientnet-b0",
		encoder_weights="imagenet",
		in_channels=3,
		classes=11,
)
model = model.to(device)
```





