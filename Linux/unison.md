From the Unison homepage:
> Unison is a file-synchronization tool for Unix and Windows. It allows two replicas of a collection of files and directories to be stored on different hosts (or different disks on the same host), modified separately, and then brought up to date by propagating the changes in each replica to the other.

So I was running training using a two workers on one machine which only had two GPUs. I was also running the evaluator on the same machine, albeit only using CPU. One run of the evaluation took more than 4 hours, so I had to run the evaluation job on a GPU. I also wanted the event files that the evaluator would create for plotting the results and graphs on Tensorboard. I also had another machine with a single GPU, but no shared storage between the two machines. Therefore, the best solution would be to run the evaluator on the second machine using the single GPU. To make it possible, I needed to have the same `model_dir` on the two machines, kept in sync. To solve this challenge, I used `unison`.

You can access Unison's Github repository using [this link](https://github.com/bcpierce00/unison), downloades page for the binareis using [this link](http://unison-binaries.inria.fr/), and the documentation using [this link](https://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html).

* First step is to download the `unison` binary on both machines and create a symlink in `/usr/bin/` to the executable. I used [this answer](https://unix.stackexchange.com/a/183299) to create the symlink.

```bash
$ sudo cp -s /home/ubuntu/tools/unison /usr/bin/unison
```

You also need to add `/home/ubuntu/tools` to the `PATH` enviroment variable.

* To synchronise the directory on the two machines, you first need to make a test remote invocation to check if things are correct.
```bash
$ ssh <remotehost> unison -version
```

The version printed should match the local version of the `unison`.

* Finally, to execute the folder sync using `unison`, you can use the following command
```bash
$ unison <localfolder> ssh://<remotehost>//home/<user>/path/to/remote/folder
```

This will compare the files between the two folders on the two remote machines and will show prompts asking for commands regarding actions it should execute on files.

This is a sample output from the program:
```bash
Looking for changes
  Waiting for changes from server
Reconciling changes

local          erfan-vm2
         <---- changed    checkpoint  [f] f
changed  <=?=>            config.json  [f] /
         <---- changed    events.out.tfevents.1534965067.erfan-vm2  [f] f
         <---- new file   model.ckpt-32036.data-00000-of-00001  [f] f
         <---- new file   model.ckpt-32036.index  [f] f
         <---- new file   model.ckpt-32036.meta  [f] f

Proceed with propagating updates? [] g
Propagating updates
```

At each line `unison` will ask you for a command. The list of command and their description is as follows:
```
Commands:
  <ret> or f or <spc>   follow unison's recommendation (if any)
  I                     ignore this path permanently
  E                     permanently ignore files with this extension
  N                     permanently ignore paths ending with this name
  m                     merge the versions
  d                     show differences
  x                     show details
  L                     list all suggested changes tersely
  l                     list all suggested changes with details
  p or b                go back to previous item
  g                     proceed immediately to propagating changes
  q                     exit unison without propagating any changes
  /                     skip
  > or .                propagate from from local to erfan-vm2
  < or ,                propagate from from erfan-vm2 to local
  ```
  
