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
