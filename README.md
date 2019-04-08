# CVFX_GAN-Dissection
  # 1.Generate images with GANPaint
  
  | orign(a)        | ADD_grass(b)          | ADD_cloud(c)  |
  | :-------------: |:-------------:| :-----:|
  | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/oriign.PNG?raw=true)        | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/ADD_grass.PNG?raw=true)      | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/ADD_cloud.PNG?raw=true) |
  | remove_grass_door(d)        | remove_tree_1(e)      |   remove_tree_2(f) |
  | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_grass_door.png?raw=true)      | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_tree_1.png?raw=true)      |   ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_tree_2.png?raw=true) |

  
  >>上面是一些我們試的東西，從圖b跟c可以看出，在地面上增加草或是在空中增加雲朵是很正常的，但是若反過來，在天空想要增加草，或是在地面想要增加雲朵，那就會出現很奇怪的圖案，另外在增加雲朵的時候附近的房屋邊緣會被模糊化。至於刪除物件如圖def所示，d是刪除草地和門，會發現草地變成水泥地，而門則是變成窗戶，都是被其他物件所取代的，然後e跟f都是刪除樹，可是e是刪中間而已，它的圖片會變得很奇怪，不過如果像f把整顆樹都刪除，圖片就會變得比較正常了。
  
  # 2.Dissect any GAN model and analyze
  
  | layer1        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer1_1.PNG"/>          | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer1_2.PNG"/>  |
| :-------------: |:-------------:| :-----:|
| layer4        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer4_1.PNG"/>      | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer4_2.PNG"/> |
| layer7       | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer7_1.PNG"/>      |   <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer7_2.PNG"/> |

  >我們在每一個layer都選出兩張照片作為代表，以living room作為示範，這些圈起來的部位是該unit注意的class。由上圖我們可以發現layer1 focus的結果不盡理想，常無法正確判斷物件，而layer4有明顯的進步，可以正確圈出位置，但有時會有較誇張的誤差，layer7則圈出一些範圍較大的物件，雖然結果較layer4好一點，但還是會有小小的誤差。


  # 3.Compare with other method
   ### PyTorch Inpainting
   >Abstract:  
  
  >>This is a novel approach for image completion that results in images that are both locally and globally consistent.With a fully-convolutional neural network, it can complete images of arbitrary resolutions by filling-in missing regions of any shape. To train this image completion network to be consistent,It use global and local context discriminators that are trained to distinguish real images from completed ones.
  >Model Architecture:  
  ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/model_v2.PNG?raw=true)  
