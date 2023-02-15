# Context Commands

Native commands in `kubectl` for context check. And substitutions for the native commands.

## Namespace
- Show current namespace
  - `kubectl config view --minify -o jsonpath='{..namespace}'`
  - Alternative is `kubectx` + `kubens` [kubectx](https://github.com/ahmetb/kubectx)