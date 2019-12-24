## APPENDIX B CODING EXAMPLES

### B.1 Examples of complete control sequences

The general format of a control sequence is:

```
CSI P1 ... Pn I1 ... Im F
```

In an 8-bit environment the control function CURSOR FORWARD by one position can
be represented in many ways. Examples are:

```
9/11 3/1 4/3
9/11 3/0 3/1 4/3
9/11 4/3
9/11 3/0 4/3
```

The second example shows that leading ZEROs (3/0) are not significant. The
third and fourth examples use the fact that a default value for CUF is defined
and is equal to l.

In a 7-bit enviroment the corresponding examples are:

```
1/11 5/11 3/1 4/3
1/11 5/11 3/0 3/1 4/3
1/11 5/11 4/3
1/11 5/11 3/0 4/3
```

In an 8-bit environment SCROLL RIGHT by 28 positions can be represented for
instance by:

```
9/11 3/2 3/8 2/0 4/1
```

In a 7-bit environment the corresponding representation is:

```
1/11 5/11 3/2 3/8 2/0 4/1
```

In an 8-bit environment DEFINE. AREA QUALIFICATION permitting
numeric and alphabetic data to be entered into an input area
can be represented by:

```
9/11 3/3 3/11 3/4 6/15
```

In a 7-bit environment the corresponding representation is:

```
1/11 5/11 3/3 3/11 3/4 6/15
```

### B.3. Examples of parameter strings

| Character Form | Bit Combination Form | Explanation |
| ---------------| ---------------------| ------------|
| 7              | 3/7                  | A parameter having the value 7. |
| 98             | 3/9 3/8              | A parameter having value 98. |
| 4;2            | 3/4 3/11 3/2         | Two parameters having values 4 and 2 respectively. |
| <3             | 3/12 3/3             | A private parameter string. |
| 2;             | 3/2 3/11             | Two parameters, the first having the value 2 and the second taking the default value. |
| ;5             | 3/11 3/5             | Two parameters, the first taking the default value and the second having the value 5. |
| 1;;4           | 3/1 3/11 3/11 3/4    | Three parameters, the first having the value 1, the second taking the default value, and the third having the value 4. |
| 0007           | 3/0 3/0 3/0 3/7      | A parameter having the value 7. |


