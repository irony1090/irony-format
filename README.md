## irony Format
---
### My collection of useful JavaScript utilities.
## Features
* Typescript
* Steady update

# Download
To install ironyFormat, use yarn
```
$ yarn add @irony0901/format
```
## Methods
* [createUuid](#createUuid)
* [numberTodataSize](#numberTodataSize)
* [hideText](#hideText)
* [equals](#equals)
* [parseTel](#parseTel)

## createUuid
### createUuid( option: CreateUuidOption )
---
#### CreateUuidOption
- length: number   
  The number of letters of the output
- prefix?: string   
  The prefix of the output
- suffix?: string   
  The suffix of the output
---
**Examples**
``` javascript
import { createUuid } from '@irony0901/format';

const example_1 = createUuid({ length: 24 });
const example_2 = createUuid({ length: 24, prefix: 'PRODUCT-' });
const example_3 = createUuid({ length: 24, suffix: ':USER' });
const example_4 = createUuid({ length: 24, prefix: 'PRODUCT-', suffix: ':USER' });
const example_5 = createUuid({ length: 3, suffix: 'PRODUCT-' });
const example_6 = createUuid({ length: 3, suffix: ':USER' });

console.log( example_1 ) // '4b0ab5ca4c2940a08002ce3c' **length is 24**
console.log( example_2 ) // 'PRODUCT-02ebdf8ff8a54862' **length is 24**
console.log( example_3 ) // 'PRODUCT-643082bba30:USER' **length is 24**
console.log( example_4 ) // '3fa6219b5290474392b:USER' **length is 24**
console.log( example_5 ) // 'PRO' **length is 3**
console.log( example_6 ) // ':US' **length is 3**

```

## numberTodataSize
### numberTodataSize( size: number )
**Examples**
``` javascript
import { numberTodataSize } from '@irony0901/format';

const kbSize = 1024;
const mbSize = KBSize * 1024;
const gbSize = MBSize * 1024;
const tbSize = GBSize * 1024;
const pbSize = TBSize * 1024;
const exceed = PBSize * 1024;

console.log( numberTodataSize(kbSize) ) // '1.00 KB'
console.log( numberTodataSize(mbSize) ) // '1.00 MB'
console.log( numberTodataSize(gbSize) ) // '1.00 GB'
console.log( numberTodataSize(tbSize) ) // '1.00 TB'
console.log( numberTodataSize(pbSize) ) // '1.00 PB'
console.log( numberTodataSize(exceed) ) // '1024.00 PB'

```

## hideText
### hideText( option: HideTextOption )
---
#### HideTextOption
- text: string   
  Input string
- excludeLength: number
  Text number to hide
- start?: 'left'|'right'   
  Starting cursor position.  
  default value 'left'
- hideChar?: string   
  Characters to replace
---
**Examples**
``` javascript
import { hideText } from '@irony0901/format';

const text = 'PRODUCT-02ebdf8ff8a54862'
console.log( hideText({ text, excludeLength: 8 }) )  // 'PRODUCT-________________'
console.log( hideText({ text, hideChar: '*', excludeLength: 8 }) ) // 'PRODUCT-****************'
console.log( hideText({ text, hideChar: '#', start: 'right', excludeLength: 8 }) ) // '################f8a54862'
```

## equals
### equals( a: any, b: any )
---
**Examples**
``` javascript
import { equals } from '@irony0901/format';

const objA = { id: 1, name: 'irony' }
const objB = { id: 1, name: 'irony' }
const objC = { name: 'irony', id: 1 }
const arrA = [ 1, 2, 3 ]
const arrB = [ 1, 2, 3 ]
const arrC = [ 3, 2, 1 ]

console.log( objA === objB ) // objA and objB is false
console.log( JSON.stringify(objA) === JSON.stringify(objB) ) // objA and objB is true
console.log( JSON.stringify(objA) === JSON.stringify(objC) ) // objA and objC is false
console.log( equals(arrA, arrB) ) // arrA and arrB is true
console.log( equals(arrA, arrC) ) // arrA and arrC is false
console.log( equals(1, 1) ) // is true
console.log( equals(1, '1') ) // is false

```

## parseTel
### parseTel( tel: string ): ParseTel
---
#### ParseTel
  - international: string   
  International number
  - format: string[]   
  Formatting array. Up to 3 elements
  - fullFormat: string   
  Input String

---
---
**Examples**
``` javascript
import { parseTel } from '@irony0901/format';

console.log( format.parseTel('01012345678') )
/**
 * {
 *  international: null,
 *  format: [ '010', '1234', '5678' ],
 *  fullFormat: '010-1234-5678'
 * }
**/

console.log( format.parseTel('010-1234-5678') )
/**
 * {
 *   international: null,
 *   format: [ '010', '1234', '5678' ],
 *   fullFormat: '010-1234-5678'
 * }
**/

console.log( format.parseTel('(12)01012345678') )
/**
 * {
 *   international: '(+12)',
 *   format: [ '010', '1234', '5678' ],
 *   fullFormat: '(+12)010-1234-5678'
 * }
**/

console.log( format.parseTel('01-01234-5678') )
/**
 * {
 *   international: null,
 *   format: [ '01', '0123', '5678' ],
 *   fullFormat: '01-0123-5678'
 * }
**/

```

## License
[MIT](LICENSE)