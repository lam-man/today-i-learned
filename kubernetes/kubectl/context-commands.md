# Context Commands

Native commands in `kubectl` for context check. And substitutions for the native commands.

## Namespace
- Show current namespace
  - `kubectl config view --minify | grep namespace`
  - Alternative is `kubectx` + `kubens` [kubectx](https://github.com/ahmetb/kubectx)
- Set namespace
  - `kubectl config set-context --current --namespace=<namespace>`
  - Alternative is `kubens <namespace>`