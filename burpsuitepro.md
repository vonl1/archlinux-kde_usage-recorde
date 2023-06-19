# `yay -S burpsuite-pro`

# Latest Support 2022.8.5
# `.jar` file preference

# download these
[keygen.jar](https://github.com/SNGWN/Burp-Suite/blob/main/keygen.jar)

[loader](https://github.com/SNGWN/Burp-Suite/blob/main/loader.jar)

# arch burpsuit locate /usr/share/burpsuite-pro/
```shell
cd /usr/share/burpsuit-pro/
sudo cp BurpSuiteLoader.jar /usr/share/burpsuit-pro/
sudo cp burp-keygen-scz.jar /usr/share/burpsuit-pro/

java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:loader.jar -noverify -jar burpsuite_pro_v2022.8.5.jar
java -jar burp-keygen-scz.jar


vim /etc/bash.bashrc

+ alias burpsuit='cd /usr/share/burpsuit-pro/ & java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:loader.jar -noverify -jar burpsuite_pro_v2022.8.5.jar'
```
then you can run burpsuit pro in terminal just one command

>[https://www.ddosi.org/burpsuite2021-8-3/](https://github.com/SNGWN/Burp-Suite)
