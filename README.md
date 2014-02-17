[ Summary ]
And implementation of DoubleArray in Common Lisp
· Because of (unsigned-byte 24), the upper limit of the storage element number several million about the type of BASE

[ Version ]
- 0.0.1


[API]

PACKAGE # dabase
Main package

FUNCTION # (build entries output-file) ->: done

It takes a list of key-value pairs , and export to a file to build a DouleArray
- Entries: key-value pairs . Needs to be unique and sorted the key .
Type of the key string or (array (unsigned-byte 8)).
※ It is not possible to include the 255 null character (0) and the key
             The value type (unsigined-byte 24)
- Output-file: path of the file to output the DoubleArray was constructed

FUNCTION # (load index-file-path) -> da

I read from a file DoubleArray
- Index-file-path: save file of DoubleArray built with build function
- The da: DoubleArray read

FUNCTION # (element-count da) -> fixnum

I returns the number of elements stored in DoubleArray
- Da: DoubleArray

FUNCTION # (member key da & key (start 0) (end (length key))?) -> Boolean

Determining key whether the specified stored in DoubleArray
- Key: key to be used in the search . string or (array (unsigned-byte 8))
- Da: DoubleArray
- Start: start position of the key in
- End: the end position of the key in

FUNCTION # (get key da & key (start 0) (end (length key))) -> nil or fixnum

I get the value associated with this mapping, the specified key . Nil is returned if the key does not exist
- Key: key to be used in the search . string or (array (unsigned-byte 8))
- Da: DoubleArray
- Start: start position of the key in
- End: the end position of the key in

MACRO # (each-common-prefix (value position)
                           (key da & key (start 0) (end (length key)))
                           & body body) -> nil

I do a common prefix search
For the key of all the prefix matches , with bound value, the position variable each match position and values, you can perform a body
- Value: the value of the variable key prefix matches is bound . it is used in the body evaluation
- Position: variable bound match the position of the key . it is used in the body evaluation
- Key: key to be used in the search . string or (array (unsigned-byte 8))
- Da: DoubleArray
- Start: start position of the key in
- End: the end position of the key in
- Body: expressions that can be evaluated and executed when the key prefix match is found


- src1# http://d.hatena.ne.jp/sile/20100627
