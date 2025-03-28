## 1. 函数定义
我们要拟合的复杂函数为 y=sin(x)+0.5cos(2x)+0.2sin(3x)。这个函数结合了不同频率的正弦和余弦函数，具有一定的复杂性和波动性，适合用于测试神经网络的拟合能力。
## 2. 数据采集
训练数据：使用 torch.linspace(-5, 5, 100) 生成了 100 个在区间 [−5,5]上均匀分布的点作为输入 x，然后将这些点代入复杂函数中计算得到对应的输出 y，从而得到训练数集。
测试数据：使用 torch.linspace(-5, 5, 200) 生成了 200 个在区间 [−5,5]上均匀分布的点作为测试输入，计算对应的真实输出用于评估模型的拟合效果。
## 3. 模型描述
我们使用的是一个两层 ReLU 神经网络，具体结构如下：输入层：接收一个输入特征（即 x 的值）。
第一个隐藏层：包含 50 个神经元，使用 ReLU 激活函数引入非线性。
第二个隐藏层：同样包含 50 个神经元，也使用 ReLU 激活函数。
输出层：输出一个值，即预测的 y 值。
模型的参数通过 Adam 优化器进行更新，损失函数使用均方误差损失（MSE），它衡量了预测值与真实值之间的平均平方误差。
## 4. 拟合效果
训练过程：在训练过程中，模型的损失随着训练轮数（epoch）的增加而逐渐减小。从打印的损失值可以看出，随着训练的进行，模型逐渐学习到了函数的模式，损失不断降低。
可视化结果：通过绘制实际数据点和拟合曲线的图形，我们可以直观地看到模型的拟合效果。在大多数情况下，拟合曲线能够较好地逼近实际数据点，说明模型能够捕捉到复杂函数的主要特征。然而，在某些波动较大的区域，可能会存在一定的误差，但总体上模型能够对复杂函数进行有效的拟合。
综上所述，两层 ReLU 神经网络在拟合复杂函数 y=sin(x)+0.5cos(2x)+0.2sin(3x) 方面表现出了较好的性能，能够在一定程度上逼近真实函数。通过调整模型的结构（如增加隐藏层神经元数量、增加隐藏层数量）和训练参数（如学习率、训练轮数），可能会进一步提高拟合效果。