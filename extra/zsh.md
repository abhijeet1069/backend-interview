# ZSH

## show history with timestamps

```zsh
history -E
  998  24.10.2026 08:56  open ~
  999  24.10.2026 08:56  fc -lh 1
 1000  24.10.2026 08:56  fc -lh 1
 1001  24.10.2026 08:57  history
 1002  24.10.2026 08:57  history -E
```

## encode decode base64

```zsh
# encode
echo null | base64
  bnVsbAo=

#decode
echo bnVsbAo= | base64 --decode
  null
```

## curl request

```zsh
curl -H "Authorization: Basic dxNlcjo5m2Ew" http://localhost:8080/hello
```