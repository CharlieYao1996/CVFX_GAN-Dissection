# CVFX_GAN-Dissection
  # 1.Generate images with GANPaint
  >### oriign(a)
  >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/oriign.PNG?raw=true)
  >### ADD_grass(b)
  >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/ADD_grass.PNG?raw=true)
  >### ADD_cloud(c)
  >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/ADD_cloud.PNG?raw=true)
  >### remove_grass_door(d)
  >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_grass_door.png?raw=true)
  >### remove_tree_1(e)
  >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_tree_1.png?raw=true)
  >### remove_tree_2(f)
  >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/remove_tree_2.png?raw=true)
  >>上面是一些我們試的東西，從圖b跟c可以看出，在地面上增加草或是在空中增加雲朵是很正常的，但是若反過來，在天空想要增加草，或是在地面想要增加雲朵，那就會出現很奇怪的圖案，另外在增加雲朵的時候附近的房屋邊緣會被模糊化。至於刪除物件如圖def所示，d是刪除草地和門，會發現草地變成水泥地，而門則是變成窗戶，都是被其他物件所取代的，然後e跟f都是刪除樹，可是e是刪中間而已，它的圖片會變得很奇怪，不過如果像f把整顆樹都刪除，圖片就會變得比較正常了。
<table>
    <tr>
        <th>Layer</th>
        <th>1</th>
        <th>2</th>
    </tr>
    <tr>
        <th>Layer1</th>
        <td> >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer1_1.PNG?raw=true) </td>
        <td> >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer1_2.PNG?raw=true) </td>
    </tr>
    <tr>
        <th>Layer4</th>
        <td> >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer4_1.PNG?raw=true) </td>
        <td> >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer4_2.PNG?raw=true) </td>
    </tr>
    <tr>
        <th>Layer7</th>
        <td> >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer7_1.PNG?raw=true) </td>
        <td> >![image](https://github.com/CharlieYao1996/CVFX_GAN-Dissection/blob/master/layer7_2.PNG?raw=true) </td>
    </tr>
</table>
