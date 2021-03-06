# CVFX_GAN-Dissection
  # 1.Generate images with GANPaint
  
  | orign(a)        | ADD_grass(b)          | ADD_cloud(c)  |
  | :-------------: |:-------------:| :-----:|
  | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/oriign.PNG?raw=true)        | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/ADD_grass.PNG?raw=true)      | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/ADD_cloud.PNG?raw=true) |
  | remove_grass_door(d)        | remove_tree_1(e)      |   remove_tree_2(f) |
  | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_grass_door.png?raw=true)      | ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_tree_1.png?raw=true)      |   ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_tree_2.png?raw=true) |

  
上面是一些我們試的東西，從圖b跟c可以看出，在地面上增加草或是在空中增加雲朵是很正常的，但是若反過來，在天空想要增加草，或是在地面想要增加雲朵，那就會出現很奇怪的圖案，另外在增加雲朵的時候附近的房屋邊緣會被模糊化。至於刪除物件如圖def所示，d是刪除草地和門，會發現草地變成水泥地，而門則是變成窗戶，都是被其他物件所取代的，然後e跟f都是刪除樹，可是e是刪中間而已，它的圖片會變得很奇怪，不過如果像f把整顆樹都刪除，圖片就會變得比較正常了。
  
  # 2.Dissect any GAN model and analyze
  
  | layer1        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer1_1.PNG"/>          | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer1_2.PNG"/>  |
| :-------------: |:-------------:| :-----:|
| layer4        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer4_1.PNG"/>      | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer4_2.PNG"/> |
| layer7       | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer7_1.PNG"/>      |   <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer7_2.PNG"/> |

我們在每一個layer都選出兩張照片作為代表，以living room作為示範，這些圈起來的部位是該unit注意的class。由上圖我們可以發現layer1 focus的結果不盡理想，常無法正確判斷物件，而layer4有明顯的進步，可以正確圈出位置，但有時會有較誇張的誤差，layer7則圈出一些範圍較大的物件，雖然結果較layer4好一點，但還是會有小小的誤差。


  # 3.Compare with other method
   ## Globally and Locally Consistent Image Completion
   ### Abstract:  
  
  >This is a novel approach for image completion that results in images that are both locally and globally consistent.With a fully-convolutional neural network, it can complete images of arbitrary resolutions by filling-in missing regions of any shape. To train this image completion network to be consistent,It use global and local context discriminators that are trained to distinguish real images from completed ones.
  ### Model Architecture:  
  ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/model_v2.png?raw=true)
 
  ### Result:
  ![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/result_1.png?raw=true)

|              | Ex1          | Ex2           | Ex3   |
|:------------:|:------------:|:-------------:|:-----:|
| Origin       | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r1-1.png"/>        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r2-1.png"/>      | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r3-1.png"/> |
| Input        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r1-2.png"/>        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r2-2.png"/>      |  <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r3-2.png"/> |
| Ouput        | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r1-3.png"/>      | <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r2-3.png"/>      |   <img width="150" height="150" src="https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/r3-3.png"/> |


在結果可以看出來，Mask住的東西，在小範圍的情況下移除物件的效果是滿好的，但是在大範圍的情況下，可能在最後的結果會相對模糊，且由於填補畫面缺失是基於content aware fill的之下，在edge顏色複雜或是多變的情況下，填補的效果也會越來越差。


 # 4.Conclusion
  
 **GANPaint**的GUI操作介面給使用者非常方便且直覺得操作，但只能操作網站上的圖片、結果，無法根據觀察training過程來解釋model的缺失或是可改進的部分，如需觀察則網頁版則較不適合使用。且GANPaint在細部的調整我們認為還是有很大部分的改善空間，像是圖像較複雜時操作所生成的樹、門等都可能不符合我們的需求。
  
 **GAN Dissection**在我們實際操作下，可以分析多個layer中的Dissection並且找出Intervention。再根據兩參數來調整畫面的變化，是適合用於我們來觀看model的學習結果以及在各層情況下的合理性。
  
 **Globally and Locally Consistent Image Completion**則是基於GAN網路，利用Global和Local的discriminators來區分真實圖像以及完整圖像，可以生成多樣性的場景，但是最後會受到Mask的限制，如內容2.中提出，在edge顏色複雜或是多變的情況下填補的狀況會越來越差。
