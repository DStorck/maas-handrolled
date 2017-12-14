#  maas partially handrolled
a set of scripts, configs and a README to deploy a kraken configured kubernetes cluster to MAAS controlled hardware

## Pre-requistes for the machine to operate this README from
1. Mac or Linux based machine
    - only tested on Mac so far
1. modern web browser is installed
1. python 2.7.x is installed
1. pip is installed
1. docker is installed

##  Manual in MAAS GUI
1. Log into your MAAS GUI
1. Select 5 nodes for kubernetes.  All nodes should have at least 2 cores and 4GB of
  memory, more of either resource is fine.
1. Tag the five nodes.  Either select node -> tags -> edit , or node -> configuration -> machine configuration -> edit. Tag them as:
    - etcd (x1)
    - master (x1)
    - worker (x3)
1. Get your MAAS key.  This can be found in your user's settings page.  Should be a long string with two colons in it, like so:
     `DpJenPsPW7ff9Ba8vq:avuGHMffffLRQZ7Kz8:TjSa4QmER7fffffCg2WqJmfzePstcmtk`

##  Python script
1. export two variables to the shell environment you will be running `mass_handrolling.py` from:
    - `MAAS_API_URL` this is the API endpoint for your MAAS install.  This should be of the form `http<s>://DNS/MAAS/api/2.0`, the IP instead of a DNS entry is fine
    - `MAAS_API_KEY` the MAAS key from the previous section
1. Install required python libraries
    - `pip install -r requirements.txt`
1. Execute the script `maas_handrolling.py` located in this directory
    - `./maas_handrolling.py`
1. That's it!

## Using the kubernetes cluster
1. Make sure you have `kubectl` version 1.8.1 or later installed
1. `kubectl --kubeconfig=$HOME/.kraken/maas/admin.kubeconfig get nodes` or whatever commands you would like to run

##  Getting Support
please go to the #kraken channel on http://slack.k8s.io
