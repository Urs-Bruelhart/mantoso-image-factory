# Ansible

NOTE: Do not use Ansible `raw` commands because some have [Mitogen](https://mitogen.networkgenomics.com/ansible_detailed.html) setup via environment variables.
      Ideally we would use it to install `python3` if it is not installed, but [Mitogen needs Python already on the target](https://mitogen.networkgenomics.com/ansible_detailed.html#noteworthy-differences).
