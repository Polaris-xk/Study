E27706

```python
ipt=[str(x) for x in input().split()]
stack=[]
ans=[]
for j in range(len(ipt)):
    stack.append(ipt[j])
while stack:
    i=stack.pop()
    ans.append(i)
print(' '.join(ans))
```

E27951

```python
MNlst=[int(x) for x in input().split()]
M,N=MNlst[0],MNlst[1]
word_lst=[int(x) for x in input().split()]
instack=[]
count=0
for i in range(N):
    ipt=word_lst[i]
    if ipt not in instack:
        instack.append(ipt)
        count+=1
    if len(instack)>M:
        instack.pop(0)
print(count)
```

M27948

```python
class Node:
    def __init__(self,val):
        self.value=val
        self.left=None
        self.right=None

    def postorder(self):
        rtn=[]
        if self.left:
            rtn.extend(self.left.postorder())
        if self.right:
            rtn.extend(self.right.postorder())
        rtn+=[self.value]
        return rtn

def BuildTree(astr,n):
    if n==0:
        if astr=='1':
            typ='I'
        else:
            typ='B'
        node=Node(typ)
        return node
    else:
        leftchild=BuildTree(astr[:2**(n-1)],n-1)
        rightchild=BuildTree(astr[2**(n-1):],n-1)
        if leftchild.value==rightchild.value:
            typ=leftchild.value
        else:
            typ='F'
        node=Node(typ)
        node.left=leftchild
        node.right=rightchild
        return node

N=int(input())
S=str(input())
Tree=BuildTree(S,N)
print(''.join(Tree.postorder()))
```

T27925

```python
class queue:
    def __init__(self,v):
        self.que=[]
        self.name=v

    def show_que(self):
        s=[]
        for x in self.que:
            s.append(x.name)
        return s

t=int(input())
teams_lst=[]
people={}
for _ in range(t):
    ateam=[int(x) for x in input().split()]
    for p in ateam:
        people[p]=_+1
ans_lst=[]
Queue=queue('all')
while True:
    ipt=[x for x in input().split()]
    if len(ipt)==2:
        pe=int(ipt[1])
        tm=people[pe]
        if tm in Queue.show_que():
            idx=Queue.show_que().index(tm)
            Queue.que[idx].que.append(pe)
        else:
            it=queue(tm)
            it.que.append(pe)
            Queue.que.append(it)
    else:
        if ipt[0]=='DEQUEUE':
            a=Queue.que[0].que.pop(0)
            if Queue.que[0].que==[]:
                Queue.que.pop(0)
            ans_lst.append(a)
        else:
            break
for x in ans_lst:
    print(x)
```

27928

```python
def traversal(root):
    ans = []
    chd = node_dct[root].copy()
    if not chd:
        return [root]
    else:
        while chd:
            new_root = chd.pop(0)
            if new_root < root:
                ans.extend(traversal(new_root))
            else:
                chd.insert(0,new_root)
                break
        ans.append(root)
        while chd:
            new_root = chd.pop(0)
            ans.extend(traversal(new_root))
        return ans


def find_root(p):
    if p not in root_lst:
        return p
    else:
        return find_root(parent_dct[p])

n = int(input())
node_dct = {}
parent_dct = {}
for i in range(n):
    ipt = [int(x) for x in input().split()]
    root = ipt.pop(0)
    children = sorted(ipt)
    node_dct[root] = children

    for x in children:
        parent_dct[x] = root
root_lst = list(parent_dct.keys())
Root = find_root(root_lst[0])
ans = traversal(Root)
for i in ans:
    print(i)
```

27932（unsolved）

```python
import heapq

nklst=[int(x) for x in input().split()]
n,k=nklst[0],nklst[1]
data=[int(x) for x in input().split()]

heapq.heapify(data)

std_data=[]
while data:
    std_data.append(heapq.heappop(data))

stack=[]
while std_data:
    stack.append(std_data.pop(0))
    if len(stack)==k:
        break
if len(stack)==k:
    if std_data and std_data[0]!=stack[-1]:
        print(stack[-1])
    elif not std_data:
        print(stack[-1])
    else:
        print(-1)
else:
    if k==0:
        if stack and stack[0]>1:
            print(1)
        else:
            print(-1)
    else:
        print(-1)
```