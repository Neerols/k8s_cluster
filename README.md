1. #### Project dev-env initialization
    - note - not tested with `minikube`
    - note - read all instructions carefully especially on referenced documentation pages 
    - install docker
    - install `kubectl kubeadm kubelet` [Installing kubeadm]
    - (optional) `kubectl` autocompletion [Enabling shell autocompletion]
    - disable swap `sudo swapoff -a`, `sudo vim /etc/fstab` and put(comment) `#` before swap partition
    - follow the instruction on [Installing a Pod network add-on] short explanation below
        * `sudo kubeadm init --pod-network-cidr=172.96.0.0/16` follow instructions at the end of process
        * connect kubectl with cluster [Connect kubectl]
        * apply Pod network add-on `Calico` [Installing a Pod network add-on]
        * don't forget to change pod network by downloading the yml file and change parameters of CIDR on step 2!
        * add pod scheduling ability [Running pods]
    - check ./deploy/db-service.yaml,./deploy/local-service.yaml for local deploy config params
    - check ./jobs/env/docker-secret.yml, ./jobs/env/gradle-cache-volume.yml, ./jobs/env/project-volume.yml for local build config params
    - apply(`kubectl apply -f`) all `db*` and `local*` configurations in /deploy
    - apply(`kubectl apply -f`) all configurations in /jobs/env
    - `project-run.sh` builds and runs project in cluster


[Install kubectl on Linux]: https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux
[Enabling shell autocompletion]: https://kubernetes.io/docs/tasks/tools/install-kubectl/#enabling-shell-autocompletion
[Installing kubeadm]: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/
[Connect kubectl]: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/#more-information
[Installing a Pod network add-on]: https://docs.projectcalico.org/getting-started/kubernetes/quickstart
[Running pods]: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/#control-plane-node-isolation
