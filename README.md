# PLEASE ONLY CONTRIBUTE WITH THE EXPECTATION THAT 100% OF THIS REPO TO BE DELETED BY 2021-06-01

- We're big on keeping our commitments, but we may break this one
- that said, it's a good assumption that nothing you do here will last in any way other than for archival purposes

# Code Release O(Soon)
2021-04-22: We had hoped to clear all the hurdles shortly, but we're not quite there yet. Stay tuned!

## User experience

Our goal is to have a user experience that looks like this:

```bash
# Local experience
# Install same CLI & configure K8s cluster (as easy as pip install foobaz)
$ export SAME_ENVIRONMENT=local
$ curl http://projectsame.org/install.sh | bash
```

The above:

- Downloads and installs a CLI tool
- Installs a local kubernetes API (e.g., via k3s/k3d)
- Installs Kubeflow into that cluster
- Provides an SAME endpoint inside the Kubernetes cluster that can respond to `same` commands

```bash
# Create a program in Kubernetes and populates it with the defaults generated
# by the original author. Also uploads history exported by the original author
$ same create program -f https://github.com/uoftoronto/papers/arXiv.5778v1:1.0
```

The above:

- Creates all necessary services inside the Kubernetes cluster (same experience on local and/or hosted)
- Provisions resources necessary (e.g. Premium disk, GPU notes, etc) OR clearly alerts the user that the expected provisioning is not possible
- Pushes all metadata into the chosen metadata store for future comparison

```bash
# Execute a pipeline with new parameters defined by the original author
$ same run program arXiv.1303.5778v1:1.0 --epochs=1000
```

The above:

- Executes the program previously uploaded with the override parameter of 'epochs=100'
- Remainder of the execution occurs as expectedwith the defaults
- Is _usually_ driven off a git like system
- Pushes results into expected metadata store

```bash
# Export the entire pipeline and history to a single file. Results in file 
# arXiv.1303.5778v1:1.1.tgz.
$ same export program -n arXiv.1303.5778v1:1.1
```

The above:

- Includes all necessary services and infrastructure descriptions to recreate the system anywhere
- Also offers a way to select metadata to export and include
- Does not NECESSARILY include data, but could include pointers to the data

With all this, we think we can make a breakthrough in the way that machine learning is reproduced across multiple environments.

