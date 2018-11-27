---
layout: post
title: Python Note
date: 2018-11-24
tag: AI
---

#### [np.ravel_multi_index](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ravel_multi_index.html)

#### np.arange(a,b)\[::-1]
    >>> np.arange(2,5)
    array([2, 3, 4])
    >>> np.arange(2,5)[::-1]
    array([4, 3, 2])
    >>> np.arange(2,5)[::1]
    array([2, 3, 4])

#### np.prod
    >>> np.prod((2,3))
    6
    >>> np.prod((2,3,4))
    24
    >>> np.prod((2))
    2

#### [collections.defaultdict](https://docs.python.org/2/library/collections.html#collections.defaultdict)
    import collections
    s = [('yellow', 1), ('blue', 2), ('yellow', 3), ('blue', 4), ('red', 1)]
    # defaultdict
    d = collections.defaultdict(list)
    for k, v in s:
        d[k].append(v)
    # Use dict and setdefault
    g = {}
    for k, v in s:
        g.setdefault(k, []).append(v)
    # Use dict
    e = {}
    for k, v in s:
        e[k] = v

    list(d.items())
    [('blue', [2, 4]), ('red', [1]), ('yellow', [1, 3])]
    >>> list(g.items())
    [('blue', [2, 4]), ('red', [1]), ('yellow', [1, 3])]
    >>> list(e.items())
    [('blue', 4), ('red', 1), ('yellow', 3)]
    >>> d
    defaultdict(<class 'list'>, {'blue': [2, 4], 'red': [1], 'yellow': [1, 3]})
    >>> g
    {'blue': [2, 4], 'red': [1], 'yellow': [1, 3]}
    >>> e
    {'blue': 4, 'red': 1, 'yellow': 3}
    >>> d.items()
    dict_items([('blue', [2, 4]), ('red', [1]), ('yellow', [1, 3])])
    >>> d["blue"]
    [2, 4]
    >>> d.keys()
    dict_keys(['blue', 'red', 'yellow'])
    >>> d.default_factory
    <class 'list'>
    >>> d.values()
    dict_values([[2, 4], [1], [1, 3]])

    >>> s = 'mississippi'
    >>> d = defaultdict(int)
    >>> for k in s:
    ...     d[k] += 1
    ...
    >>> list(d.items())
    [('i', 4), ('p', 2), ('s', 4), ('m', 1)]

#### [collections.deque](https://docs.python.org/2/library/collections.html#deque-objects)
    >>> from collections import deque
    >>> d = deque('ghi')                 # make a new deque with three items
    >>> for elem in d:                   # iterate over the deque's elements
    ...     print elem.upper()
    G
    H
    I

    >>> d.append('j')                    # add a new entry to the right side
    >>> d.appendleft('f')                # add a new entry to the left side
    >>> d                                # show the representation of the deque
    deque(['f', 'g', 'h', 'i', 'j'])

    >>> d.pop()                          # return and remove the rightmost item
    'j'
    >>> d.popleft()                      # return and remove the leftmost item
    'f'
    >>> list(d)                          # list the contents of the deque
    ['g', 'h', 'i']
    >>> d[0]                             # peek at leftmost item
    'g'
    >>> d[-1]                            # peek at rightmost item
    'i'

    >>> list(reversed(d))                # list the contents of a deque in reverse
    ['i', 'h', 'g']
    >>> 'h' in d                         # search the deque
    True
    >>> d.extend('jkl')                  # add multiple elements at once
    >>> d
    deque(['g', 'h', 'i', 'j', 'k', 'l'])
    >>> d.rotate(1)                      # right rotation
    >>> d
    deque(['l', 'g', 'h', 'i', 'j', 'k'])
    >>> d.rotate(-1)                     # left rotation
    >>> d
    deque(['g', 'h', 'i', 'j', 'k', 'l'])

    >>> deque(reversed(d))               # make a new deque in reverse order
    deque(['l', 'k', 'j', 'i', 'h', 'g'])
    >>> d.clear()                        # empty the deque
    >>> d.pop()                          # cannot pop from an empty deque
    Traceback (most recent call last):
      File "<pyshell#6>", line 1, in -toplevel-
        d.pop()
    IndexError: pop from an empty deque

    >>> d.extendleft('abc')              # extendleft() reverses the input order
    >>> d
    deque(['c', 'b', 'a'])
