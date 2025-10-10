|Logic Gate|primary input|SA type|stuck-at fault input|primary output|stuck-at output|failed?|
| :---: | :---: | :---: | :---: | :---: | :---: | :---: 
|BUFF|0|SA0[A]|0|0|0||
|BUFF|1|SA0[A]|0|1|0|failed|
|BUFF|0|SA1[A]|1|0|1|failed|
|BUFF|1|SA1[A]|1|1|1||
|BUFF|0|SA0[Output]|x|0|0||
|BUFF|1|SA0[Output]|x|1|0|failed|
|BUFF|0|SA1[Output]|x|0|1|failed|
|BUFF|1|SA1[Output]|x|1|1||