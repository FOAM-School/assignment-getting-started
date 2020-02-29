# Assignment for the getting-started lecture

## Goals

- Get familiarized with the created docker container.
- Practice engaging in individual assignments.

## Basic-level skills

Access your remote machine with the most basic command (The first > denotes that the user is a regular user):

```bash
> ssh -i ~/.ssh/testmachine.pem linux1@xxx.xxx.xxx.xxx
```

Where:
- `~/.ssh/testmachine.pem` should point to the path to the SSH key-pair file on
  your local machine.
- `linux1` is the user you intend to act as on the remote machine.
- `xxx.xxx.xxx.xxx` is the specific IP address of the remote machine.

### Basic system commands

At this point you're on a Red Had (more specifically, RHEL7). I want to try running
the following commands and see if you can answer the upcoming questions:

1. `df -h` to recon the filesystem
2. `lscpu` to list CPU information
3. `cat /etc/os-release` to display the content of the `/etc/os-release` file.
 
> Bu the way, you can use TAB for auto-completion :smile:

Here are the questions:

a. How much "free" disk space you have? (hint: look for the device `/dev/sda*`)
b. What is the maximal CPU frequency we can reach on this machine?
c. What OS the machine is running?

### Becoming the super user

OK, let's say I want to install a well-known text editor on the remote machine.
Now that I know for sure what kind of OS I'm on, I can run the following command
to install, say vim:

```bash
yum install vim
```

That doesn't work, huh! Regular users can't install packages system-wide. That's one
action among many that only special user account have access to.

The most powerful user on Red Had (and all other Linux distributions) is called `root`.

You can become root on the remote machine by executing the following command:

```bash
> sudo -s
```
When you want to get back to your regular user (`linux1`), just type Ctrl-D, or
(the first `$` sign means that the following command is run as root)

```bash
$ exit
```

You should now be able to install a couple of recommended packages:

```bash
> sudo -s
$ yum install vim tmux
```

### Getting Attached to the docker container

If you have followed what we did in the lecture video, the script we used to install docker
and create our OpenFOAM container should have instantiated the container and left it running
in the background.

The most basic method to attach to an interactive shell on that container is to run (as root):

```bash
$ docker -it fe4 bash
```

where:
- `-it` tells docker to create an interactive terminal
- `fe4` is the name of the target container
- `bash` is the command to run: the shell command!

You'll be presented with a prompt similar to this:
```bash
root@containerid:~/foam/foam-extend-4/ $
```
This tels as:
- We are acting as `root` inside the container with the unique id `containerid`.
- the current directory is `/root/foam/foam-extend-4`

Try to run the same commands we ran back in the **Basic system commands** section and
answer the same questions.

> At this point, you should press Ctrl-D multiple times until you leave the SSH system

## Intermediate-level skills

## Advanced-level skills
