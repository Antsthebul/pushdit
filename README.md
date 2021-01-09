# Usage of **pushd**, **popd**, **pushit**

**pushd** is a tool that stores directories in a queue. <b>Directories MUST EXIST. </b>This works in a similar fashion to the linux pushd command. `pushd` will echo the CWD as well as the directories that have been added to the queue. This is similar to the operatation of the  `dirs` linux command. The list of directories that `pushd` echoes, will be displayed in the order they were inserted, <b>0</b> being most recent. This is the order they will be *popped* on default operation, when calling `popd()`. 
```
>>> pushd('pushtest1', chdir=False)

>>> pushd('pushtest', right=True, chdir=False)

>>> pushd
- C:\Users\Antsthebul\Desktop\home;
0 home
1 pushtest1
2 pushtest
```
The way to use pushd is like pushd in linux. 
```
>>> pushd('pushtest')
```

The advantage is the functionality of adding dirs to the front or back of the queue.
```
>>> pushd('pushtest/pushtest1', right=True)
```
Now type `popd()` to simply remove the directoriy at the end of the queue or use specify if you want to remove the dir at the front. Use pushit() [no args] in a context manger and it will change to the dir next in the queue and remove that dir from the queue while staying inside the cwd. pushit( <..file>) in a context manager is also ok too, this dir will be the dir used. It supports nested with-statements to allow to easily run code in different locations of the stack and returning to the cwd at the end of the outher-mostl with block.
 
For-loops can be used to allow no dir change and no removal For a in pushd