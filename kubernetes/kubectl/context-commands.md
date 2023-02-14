# Context Commands

Native commands in `kubectl` for context check. 

## Namespace
- Show current namespace
  - `kubectl config view --minify -o jsonpath='{..namespace}'`