.. _cn_api_fluid_layers_not_equal:

not_equal
-------------------------------

.. py:function:: paddle.fluid.layers.not_equal(x, y, cond=None)

该OP逐元素地返回 :math:`x != y` 的逻辑值，使用重载算子 `!=` 可以有相同的计算函数效果。

参数：
    - **x** (Variable) – 进行比较的第一个输入，是一个多维的Tensor，数据类型可以是float32，float64，int32，int64。 
    - **y** (Variable) – 进行比较的第二个输入，是一个多维的Tensor，数据类型可以是float32，float64，int32，int64。
    - **cond** (Variable，可选) – 如果为None，则创建一个Tensor来作为进行比较的输出结果，该Tensor的shape和数据类型和输入x一致；如果不为None，则将Tensor作为该OP的输出，数据类型和数据shape需要和输入x一致。默认值为None。 
    - **force_cpu** (bool，可选) – 是否强制将输出Tensor存储在CPU。默认值为None，表示将输出Tensor存储在CPU内存上；如果为False，则将输出Tensor存储在运行设备内存上。

返回：输出结果的Tensor，数据的shape和输入x一致。

返回类型：变量（Variable），数据类型为bool类型。

**代码示例**:

.. code-block:: python

     import paddle.fluid as fluid
     import paddle.fluid.layers as layers
     import numpy as np
     label = fluid.layers.assign(np.array([3, 3], dtype="int32"))
     limit = fluid.layers.assign(np.array([3, 2], dtype="int32"))
     out_cond = fluid.layers.assign(np.array([1, 2], dtype="int32"))
     out = fluid.layers.not_equal(x=label, y=limit) # out=[False, True]
     out1 = fluid.layers.not_equal(x=label, y=limit, cond=out_cond) #out1=[False, True] out_cond=[False, True]
     out2 = fluid.layers.not_equal(x=label, y=limit, force_cpu=False) #out2=[False, True]
     out3 = label != limit #out3=[False, True]




