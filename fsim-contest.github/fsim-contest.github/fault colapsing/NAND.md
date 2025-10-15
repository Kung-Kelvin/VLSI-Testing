|Logic Gate|primary input <br> AB|SA type |stuck-at fault input <br> AB|primary output|stuck-at output|failed?|
| :---: | :---: | :---: | :---: | :---: | :---: | :---: 
|NAND|00|SA0[A]|00|1|1||
|NAND|01|SA0[A]|01|1|1||
|NAND|10|SA0[A]|00|1|1||
|NAND|11|SA0[A]|01|0|1|failed|
|NAND|00|SA1[A]|10|1|1||
|NAND|01|SA1[A]|11|1|0|failed|
|NAND|10|SA1[A]|10|1|1||
|NAND|11|SA1[A]|11|0|0||
|NAND|00|SA0[B]|00|1|1||
|NAND|01|SA0[B]|00|1|1||
|NAND|10|SA0[B]|10|1|1||
|NAND|11|SA0[B]|10|0|1|failed|
|NAND|00|SA1[B]|01|1|1||
|NAND|01|SA1[B]|01|1|1||
|NAND|10|SA1[B]|11|1|0|failed|
|NAND|11|SA1[B]|11|0|0||
|NAND|00|SA0[Output]|xx|1|0|failed|
|NAND|01|SA0[Output]|xx|1|0|failed|
|NAND|10|SA0[Output]|xx|1|0|failed|
|NAND|11|SA0[Output]|xx|0|0||
|NAND|00|SA1[Output]|xx|1|1||
|NAND|01|SA1[Output]|xx|1|1||
|NAND|10|SA1[Output]|xx|1|1||
|NAND|11|SA1[Output]|xx|0|1|failed|