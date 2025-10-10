|Logic Gate|primary input|SA type|stuck-at fault input|primary output|stuck-at output|failed?|
| --- | --- | --- | --- | --- | --- | --- 
|NAND|00|SA0|00|1|1||
|NAND|01|SA0|00|1|1||
|NAND|10|SA0|00|1|1||
|NAND|11|SA0|00|0|1|failed|
|NAND|00|SA1|01|1|1||
|NAND|01|SA1|01|1|1||
|NAND|10|SA1|01|1|1||
|NAND|11|SA1|01|0|1|failed|
|NAND|00|SA0|10|1|1||
|NAND|01|SA0|10|1|1||
|NAND|10|SA0|10|1|1||
|NAND|11|SA0|10|0|1|failed|
|NAND|00|SA1|11|1|0|failed|
|NAND|01|SA1|11|1|0|failed|
|NAND|10|SA1|11|1|0|failed|
|NAND|11|SA1|11|0|0||
|NAND|00|SA0|xx|1|1||
|NAND|01|SA0|xx|1|1||
|NAND|10|SA0|xx|1|1||
|NAND|11|SA0|xx|0|1|failed|
|NAND|00|SA1|xx|1|0|failed|
|NAND|01|SA1|xx|1|0|failed|
|NAND|10|SA1|xx|1|0|failed|
|NAND|11|SA1|xx|0|0||