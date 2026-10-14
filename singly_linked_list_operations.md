# Algorithm: Singly Linked List Operations

## Main Program

```text
START

REPEAT
    Display "1. Insert at first"
    Display "2. Insert at last"
    Display "3. Insert after a key"
    Display "4. Delete from the front"
    Display "5. Delete from the end"
    Display "6. Delete a key"
    Display "7. Display"
    Display "8. Exit"

    Read N

    SWITCH N
        CASE 1:
            CALL insertFirst()
        CASE 2:
            CALL insertLast()
        CASE 3:
            CALL insertKey()
        CASE 4:
            CALL deleteFirst()
        CASE 5:
            CALL deleteLast()
        CASE 6:
            CALL deleteKey()
        CASE 7:
            CALL display()
        CASE 8:
            Display "Have a nice day"
            EXIT
        DEFAULT:
            Display "Invalid operation"
    END SWITCH
UNTIL N = 8

STOP
```

## 1. Insert at First — insertFirst()

```text
START
Allocate memory for TEMP

IF TEMP = NULL THEN
    Display "Memory underflow"
ELSE
    Read ITEM
    TEMP.DATA = ITEM
    TEMP.LINK = HEAD
    HEAD = TEMP
END IF

CALL display()
STOP
```

## 2. Insert at Last — insertLast()

```text
START
Allocate memory for TEMP

IF TEMP = NULL THEN
    Display "Memory underflow"
    EXIT
END IF

Read ITEM

IF HEAD = NULL THEN
    TEMP.DATA = ITEM
    TEMP.LINK = HEAD
    HEAD = TEMP
ELSE
    PTR = HEAD
    WHILE PTR.LINK != NULL DO
        PTR = PTR.LINK
    END WHILE

    PTR.LINK = TEMP
    TEMP.DATA = ITEM
    TEMP.LINK = NULL
END IF

CALL display()
STOP
```

## 3. Insert After a Key — insertKey()

```text
START
Allocate memory for TEMP

IF TEMP = NULL THEN
    Display "Memory underflow"
    EXIT
END IF

Read ITEM
Read KEY
PTR = HEAD

WHILE PTR.DATA != KEY AND PTR.LINK != NULL DO
    PTR = PTR.LINK
END WHILE

IF PTR.LINK = NULL THEN
    Display "Search fails"
ELSE
    TEMP.DATA = ITEM
    TEMP.LINK = PTR.LINK
    PTR.LINK = TEMP
END IF

CALL display()
STOP
```

## 4. Delete from the Front — deleteFirst()

```text
START
IF HEAD = NULL THEN
    Display "The list is empty"
    EXIT
END IF

Display HEAD.DATA, "is deleted"
PREV = HEAD
HEAD = HEAD.LINK
Free PREV

CALL display()
STOP
```

## 5. Delete from the End — deleteLast()

```text
START
IF HEAD = NULL THEN
    Display "The list is empty"
    EXIT
END IF

PREV = HEAD
CURRENT = HEAD

WHILE CURRENT.LINK != NULL DO
    PREV = CURRENT
    CURRENT = CURRENT.LINK
END WHILE

PREV.LINK = NULL
Display CURRENT.DATA, "is deleted"
Free CURRENT

CALL display()
STOP
```

## 6. Delete a Key — deleteKey()

```text
START
IF HEAD = NULL THEN
    Display "The list is empty"
    EXIT
END IF

Read KEY
PREV = HEAD
CURRENT = HEAD

WHILE CURRENT.DATA != KEY AND CURRENT.LINK != NULL DO
    PREV = CURRENT
    CURRENT = CURRENT.LINK
END WHILE

IF CURRENT.LINK = NULL THEN
    Display "Search fails"
ELSE
    Display CURRENT.DATA, "is deleted"
    PREV.LINK = CURRENT.LINK
END IF

CALL display()
STOP
```

## 7. Display — display()

```text
START
IF HEAD = NULL THEN
    Display "the list is empty"
ELSE
    PTR = HEAD
    WHILE PTR != NULL DO
        Display PTR.DATA
        PTR = PTR.LINK
    END WHILE
END IF
STOP
```
