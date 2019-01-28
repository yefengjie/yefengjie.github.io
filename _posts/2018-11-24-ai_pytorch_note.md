---
layout: post
title: Pytorch Note
date: 2018-12-13
tag: AI
---

### [pytorch.data vs pytorch.detach()](https://github.com/pytorch/pytorch/issues/6990)
"However, .data can be unsafe in some cases. Any changes on x.data wouldn’t be tracked by autograd, and the computed gradients would be incorrect if x is needed in a backward pass. A safer alternative is to use x.detach(), which also returns a Tensor that shares data with requires_grad=False, but will have its in-place changes reported by autograd if x is needed in backward."

### view
    >>> import torch
    >>> a=torch.Tensor(2,3)
    >>> a
    tensor([[ 0.0000,  0.0000,  0.0000],
            [-0.0000,  0.0000,  2.0000]])
    >>> a.view(1,-1)
    tensor([[ 0.0000,  0.0000,  0.0000, -0.0000,  0.0000,  2.0000]])

### squeeze vs unsqueeze
    >>> b=torch.Tensor(1,3)
    >>> b.shape
    torch.Size([1, 3])
    >>> b
    tensor([[0.0000, 0.0000, 0.0000]])
    >>> b.squeeze(0)
    tensor([0.0000, 0.0000, 0.0000])
    >>> b.squeeze(0).shape
    torch.Size([3])
    >>> b.reshape(3,1)
    tensor([[0.0000],
            [0.0000],
            [0.0000]])
    >>> b.shape
    torch.Size([1, 3])
    >>> b=b.reshape(3,1)
    >>> b.shape
    torch.Size([3, 1])
    >>> b.squeeze(1)
    tensor([0.0000, 0.0000, 0.0000])
    >>> b.squeeze(1).shape
    torch.Size([3])
    >>> b.squeeze(1).unsqueeze(1).shape
    torch.Size([3, 1])
### max
params one is max value,params two is index

    >>> d=torch.Tensor([[1,3],[2,4]])
    >>> d
    tensor([[1., 3.],
            [2., 4.]])
    >>> torch.max(d,0)
    (tensor([2., 4.]), tensor([1, 1]))
    >>> torch.max(d,1)
    (tensor([3., 4.]), tensor([1, 1]))

### [gather](https://pytorch.org/docs/stable/torch.html)
    >>> b = torch.Tensor([[1,2,3],[4,5,6]])
    >>> index_1 = torch.LongTensor([[0,1],[2,0]])
    >>> index_2 = torch.LongTensor([[0,1,1],[0,0,0]])
    >>> b
    tensor([[1., 2., 3.],
            [4., 5., 6.]])
    >>> index_1
    tensor([[0, 1],
            [2, 0]])
    >>> index_2
    tensor([[0, 1, 1],
            [0, 0, 0]])
    >>> print(torch.gather(b,dim=1,index=index_1))
    tensor([[1., 2.],
            [6., 4.]])
    >>> print(torch.gather(b,dim=0,index=index_2))
    tensor([[1., 5., 6.],
            [1., 2., 3.]])
### namedtuple
    >>> a=namedtuple("Experience", field_names=["state", "action", "reward", "next_state", "done"])
    >>> c=a('1','2','3','4','5')
    >>> c.state
    '1'
### torch.size()
    >>> x = torch.Tensor(5,3)
    >>> print(x.size()[0])
    5
    >>> print(x.size()[1])
    3
### torch.view()
    >>> x = torch.randn(8, 8)
    >>> z = x.view(-1, 4)
    >>> print(x.size(), z.size())
    torch.Size([8, 8]) torch.Size([16, 4])
### torch.add_()
Returns a new tensor with the same data as the self tensor but of a different shape.

    >>> x=torch.rand(5,3)
    >>> print(x)
    tensor([[ 0.1871,  0.0850,  0.7820],
            [ 0.6210,  0.4682,  0.1488],
            [ 0.0206,  0.1116,  0.4006],
            [ 0.3125,  0.1057,  0.8730],
            [ 0.1193,  0.3052,  0.6189]])
    >>> print(x.add_(1))
    tensor([[ 1.1871,  1.0850,  1.7820],
            [ 1.6210,  1.4682,  1.1488],
            [ 1.0206,  1.1116,  1.4006],
            [ 1.3125,  1.1057,  1.8730],
            [ 1.1193,  1.3052,  1.6189]])
### torch.view_as()
View this tensor as the same size as other. self.view_as(other) is equivalent to self.view(other.size()).

    >>> a = torch.Tensor(2, 4)
    >>> b = a.view_as(torch.Tensor(4, 2))
    >>> print(a.size(),b.size())
    torch.Size([2, 4]) torch.Size([4, 2])
    >>> print(a)
    tensor([[ 0.0000,  0.0000,  0.0000, -2.0000],
            [ 0.0000,  0.0000,  0.0000,  0.0000]])
    >>> print(b)
    tensor([[ 0.0000,  0.0000],
            [ 0.0000, -2.0000],
            [ 0.0000,  0.0000],
            [ 0.0000,  0.0000]])
### torch.Tensor.cpu()
Returns a copy of this object in CPU memory.

If this object is already in CPU memory and on the correct device, then no copy is performed and the original object is returned.
### [Torch.distributions.Categorical()](https://pytorch.org/docs/stable/distributions.html)
    >>> from torch.distributions import Categorical
    >>> m = Categorical(torch.tensor([ 0.25, 0.25, 0.25, 0.25 ]))
    >>> m.sample()
    tensor(3)
### torch.cat()
    >>> A=torch.from_numpy(np.array([2,3]))
    >>> B=torch.from_numpy(np.array([6,7]))
    >>> A
    tensor([ 2,  3])
    >>> B
    tensor([ 6,  7])
    >>> torch.cat((A,B))
    tensor([ 2,  3,  6,  7])
    >>> torch.cat((A,B)).sum()
    tensor(18)
### torch.where()
    >>> A=torch.arange(0,10,1)
    >>> A
    tensor([ 0.,  1.,  2.,  3.,  4.,  5.,  6.,  7.,  8.,  9.])
    >>> torch.where(A>5,torch.full_like(A,0),A)
    tensor([ 0.,  1.,  2.,  3.,  4.,  5.,  0.,  0.,  0.,  0.])