- read
```bash
cat /home/vars |
while read line
do
var=$line && echo $var
done
```
