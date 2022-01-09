# kubectl-check
A simple kubectl plugin for checking if resources are deployed.

**This is for testing only, please do not use in production, it's still in alpha and very simple script.**

## Installation
Make this bash executable and copy the executable in a directory that is listed in the user’s PATH environment variable (ie : /usr/local/bin)

Then you can run directly it as kubectl plugin :
```bash
kubectl check -v
```
Should return the version of this plugin

## Usages
You check kustomize (with kubectl kustomize implementation) or classic yaml file. It's work on a directory, on a file and can recursive.

If you want to check helm resources :
- generate the yaml file with `helm template ...` command and check this generated file.
- check the result
It's can work but I never tested it.

If you use directly kustomize it's better to check the resources with the generated yaml file by kustomize (depending on your kustomize and kubectl version you can have some differences).


## Command args
```
-h, --help: This help
-v, --version: Version of kubectl-check
-q, --quiet: No stdout on kubectl diff (but stderr still here)
-n [], --namespace []: If present, the namespace scope for this CLI request
-t [], --time []: Max time in second to check that the(s) resource(s) are deployed, if not set the default is 30 (seconds)
-f [], --filename []: Filename, directory, or URL to files contains the configuration to diff
-k [], --kustomize []: Process the kustomization directory. This flag can't be used together with -f or -R.
-R [], --recursive []: Process the directory used in -f, --filename recursively. Useful when you want to manage related manifests organized within the same directory.
```
