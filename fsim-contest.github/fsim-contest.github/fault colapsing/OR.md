|Logic Gate|primary input|SA type|stuck-at fault input|primary output|stuck-at output|failed?|
| :---: | :---: | :---: | :---: | :---: | :---: | :---: 
|OR|00|SA0[A]|00|0|0||
|OR|01|SA0[A]|01|1|1||
|OR|10|SA0[A]|00|1|0|failed|
|OR|11|SA0[A]|01|1|1||
|OR|00|SA1[A]|10|0|1|failed|
|OR|01|SA1[A]|11|1|1||
|OR|10|SA1[A]|10|1|1||
|OR|11|SA1[A]|11|1|1||
|OR|00|SA0[B]|00|0|0||
|OR|01|SA0[B]|00|1|0|failed|
|OR|10|SA0[B]|10|1|1||
|OR|11|SA0[B]|10|1|1||
|OR|00|SA1[B]|01|0|1|failed|
|OR|01|SA1[B]|01|1|1||
|OR|10|SA1[B]|11|1|1||
|OR|11|SA1[B]|11|1|1||
|OR|00|SA0[Output]|xx|0|0||
|OR|01|SA0[Output]|xx|1|0|failed|
|OR|10|SA0[Output]|xx|1|0|failed|
|OR|11|SA0[Output]|xx|1|0|failed|
|OR|00|SA1[Output]|xx|0|1|failed|
|OR|01|SA1[Output]|xx|1|1||
|OR|10|SA1[Output]|xx|1|1||
|OR|11|SA1[Output]|xx|1|1||