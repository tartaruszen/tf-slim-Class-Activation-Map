# tf-slim-Class-Activation-Map
use tensorflow slim to realize  Class Activation Map in  Googlenet or other cnn

Based on Learning Deep Features for Discriminative Localization（https://arxiv.org/pdf/1512.04150.pdf）

![class activation map](https://github.com/wpydcr/tf-slim-Class-Activation-Map/blob/master/img./6874.jpg)

![result](https://github.com/wpydcr/tf-slim-Class-Activation-Map/blob/master/img./20171220111.jpg)

We can find some code of caffe model to use it, but no one realize the model.

This CAM(Class Activation Map) need change some net structure，I explicitly wrote how to modify it for use on any net.

This code based on Inception v3.

The most important part is:

`net = slim.avg_pool2d(net, [8, 8], padding='VALID',
                      scope='AvgPool_1a_8x8') #1x1x2048`
                      
`logits = slim.fully_connected(net, num_classes, activation_fn=None,
                     normalizer_fn=None, scope='fc')`
                     
`w_variables = slim.get_model_variables()[-2]#10*2048`
