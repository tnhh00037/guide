---
title: Remove Whitespace from Start and End
---
## Remove Whitespace from Start and End
To remove space in the beggining, use /^\s+/
To remove space in the end, use /\s+$/
So here's the answer:
  let hello = " Hello, World!  ";
  let result=hello.replace(/^\s+/,"").replace(/\s+$/,"");

