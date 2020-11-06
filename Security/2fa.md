---
title: 2fa Auth
author: Julian Marcos
lang: es

toc: False
---
# Generar un secret totp {-}
qrencode -m 2 -t utf8 <<<
otpauth://totp/RADIATOR:radius-test?secret=KJAUISKBKRHVECQ

# Uso {-}
oathtool --totp -b KJAUISKBKRHVECQ
