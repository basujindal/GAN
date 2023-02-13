## Pytorch code for GAN models

Combine Images and Masks and place them in a directoy JSRTcomb/comb:

```
maskpath = "../datasets/JSRT/Masks/"
imgpath = "../datasets/JSRT/Images/"
combpath = "../datasets/JSRTcomb/comb/"

for imgname in tqdm(os.listdir(maskpath)):
    msk = Image.open(maskpath + imgname)
    mask = np.expand_dims(np.array(msk)*255, axis = 2)
    image = Image.open(imgpath + imgname)
    img = np.expand_dims(np.array(image), axis = 2)
    tmp = np.zeros_like(img)
    comb = np.concatenate((img, mask, tmp), axis = 2)
    
    # print(comb.dtype, comb.shape)
    comb = Image.fromarray(comb)
    comb.save(combpath + imgname)
```

 *Training*
 ---
```
python data/GAN/main.py --model WGAN-GP \
                        --is_train True \
                        --dataroot "~/JSRTcomb" \
                        --dataset JSRT \
                        --generator_iters 40000 \
                        --cuda True \
                        --batch_size 8

```

Start tensorboard:

```
tensorboard --logdir ./logs/
```
