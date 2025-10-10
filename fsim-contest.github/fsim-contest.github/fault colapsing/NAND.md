|Logic Gate|primary input|stuck-at fault input|primary output|stuck-at output|failed?|
| --- | --- | --- | --- | --- | --- |
|NAND|00|00|1|1||
|NAND|01|00|1|1||
|NAND|10|00|1|1||
|NAND|11|00|0|1|failed|
|NAND|00|01|1|1||
|NAND|01|01|1|1||
|NAND|10|01|1|1||
|NAND|11|01|0|1|failed|
|NAND|00|10|1|1||
|NAND|01|10|1|1||
|NAND|10|10|1|1||
|NAND|11|10|0|1|failed|
|NAND|00|11|1|0|failed|
|NAND|01|11|1|0|failed|
|NAND|10|11|1|0|failed|
|NAND|11|11|0|0||
|NAND|00|xx|1|1||
|NAND|01|xx|1|1||
|NAND|10|xx|1|1||
|NAND|11|xx|0|1|failed|
|NAND|00|xx|1|0|failed|
|NAND|01|xx|1|0|failed|
|NAND|10|xx|1|0|failed|
|NAND|11|xx|0|0||