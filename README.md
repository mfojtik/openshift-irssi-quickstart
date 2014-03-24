# OpenShift irssi quickstart #

This is an example of how you can run irssi client inside your OpenShift gear.
NOTE: This is **not-supported** and there is no quarantee that your client will
not be taken down. It is more like a PoC.

## Installation ##

First, create a DIY application:

```
rhc app create irssi diy
```

(to speed up compilation you can use the 'medium' size gear if you have Silver
or Bronze account). 

Second, push this quickstart:

```
git remote add upstream -m master https://github.com/mfojtik/openshift-irssi-quickstart
git pull -s recursive -X theirs upstream master
git push
```

After this step, you should go and make a coffe as it might take up to 3-5
minutes (depends on your gear size) for irssi to compile and install.

After successfull compilation, you should have irssi running inside the tmux
session in gear. To connect, you need to first ssh into the gear:

```
rhc ssh irssi
```

and then just connect to the tmux session:

```
tmux -S $OPENSHIFT_DATA_DIR/tmux.socket tmux attach
```

If you connect for the first time, do not forget to change your IRC nick name,
otherwise the irssi will use system username which might not be valid for all
IRC servers (`/set nick joe`).`
