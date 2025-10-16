|Logic Gate|primary input <br>AB|SA type|stuck-at fault input<br>AB|primary output|stuck-at output|failed?|
| :---: | :---: | :---: | :---: | :---: | :---: | :---: 
|XNOR|00|SA0[A]|00|1|1||
|XNOR|01|SA0[A]|01|0|0||
|XNOR|10|SA0[A]|00|0|1|failed|
|XNOR|11|SA0[A]|01|1|0|failed|
|XNOR|00|SA1[A]|10|1|0|failed|
|XNOR|01|SA1[A]|11|0|1|failed|
|XNOR|10|SA1[A]|10|0|0||
|XNOR|11|SA1[A]|11|1|1||
|XNOR|00|SA0[B]|00|1|1||
|XNOR|01|SA0[B]|00|0|1|failed|
|XNOR|10|SA0[B]|10|0|0||
|XNOR|11|SA0[B]|10|1|0|failed|
|XNOR|00|SA1[B]|01|1|0|failed|
|XNOR|01|SA1[B]|01|0|0||
|XNOR|10|SA1[B]|11|0|1|failed|
|XNOR|11|SA1[B]|11|1|1||
|XNOR|00|SA0[Output]|xx|1|0|failed|
|XNOR|01|SA0[Output]|xx|0|0||
|XNOR|10|SA0[Output]|xx|0|0||
|XNOR|11|SA0[Output]|xx|1|0|failed|
|XNOR|00|SA1[Output]|xx|1|1||
|XNOR|01|SA1[Output]|xx|0|1|failed|
|XNOR|10|SA1[Output]|xx|0|1|failed|
|XNOR|11|SA1[Output]|xx|1|1||