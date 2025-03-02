fnm（Fast Node Manager） はNode.jsのバージョン管理ツール<br>
windowsではfnmでバージョン管理をするのが推奨されている。

# 導入

```
# fnmをダウンロードしてインストールする：
# install後にpowershellの再起動が必要かも
winget install Schniz.fnm

# Node.jsをダウンロードしてインストールする：
fnm install 22

# fnm useでエラーがでる場合
fnm env --use-on-cd | Out-String | Invoke-Expression

# バージョン切り替え
fnm use X.X.X

# バージョン確認
node -v
```