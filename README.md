## Pytorch code for GAN models

 *Training*
 ---
```
python data/GAN/main.py --model WGAN-GP  \
                        --is_train True \
                        --dataroot "/root/JSRT" \
                        --dataset JSRT \
                        --generator_iters 40000 \
                        --cuda True \
                        --batch_size 8 \
                        --image_size 64 \
                        --channels 3

```

```
python data/GAN/main.py --model WGAN-GP  \
                        --is_train False \
                        --dataset JSRT \
                        --cuda True \
                        --batch_size 8 \
                        --image_size 64 \
                        --channels 3 \
                        --load_G /root/generator.pkl \
                        --load_D /root/discriminator.pkl

```

Start tensorboard:

```
tensorboard --logdir ./logs/
```
