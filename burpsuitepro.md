# `yay -S burpsuite-pro`

# download these
[BurpSuiteLoader.jar](https://github.com/x-Ai/BurpSuite/blob/main/BurpSuiteLoader.jar)

[burp-keygen-scz.jar](https://github.com/x-Ai/BurpSuite/blob/main/burp-keygen-scz.jar)

# arch burpsuit locate /usr/share/burpsuite-pro/
```shell
cd /usr/share/burpsuite-pro/
sudo cp BurpSuiteLoader.jar /usr/share/burpsuite-pro/
sudo cp burp-keygen-scz.jar /usr/share/burpsuite-pro/

java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:BurpSuiteLoader.jar -noverify -jar burpsuite-pro.jar
java -jar burp-keygen-scz.jar


vim /etc/bash.bashrc

+ alias burpsuit='cd /usr/share/burpsuite-pro/ & java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:BurpSuiteLoader.jar -noverify -jar burpsuite-pro.jar'
```
>https://www.ddosi.org/burpsuite2021-8-3/
