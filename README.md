# Text-Utils

Some basic function's to clean written data using Django!

## Installation: -

* This project needs to install Django.

```python
pip install Django
```
* Django is used to make it dyanmic content.

## Functionality: -
* Remove Punctuation 
* Full Capital
* New Line Remover(extra new line remover)
* Extra-Space Remover
* Character Count

### Remove Puncuation: -

```python
if removepunc=="on":
        analyzed=""
        punctuation = '''!()-[]{};:'",<>./?@#$%^&*_~'''
        for char in djtext:
            if char not in punctuation:
                analyzed=analyzed+char 
        params={'purpose':'Removed punctuation', 'analyzed_text':analyzed}
        djtext=analyzed
```

This function removes puncuation mark's from text 
puncuation marks such as: -''!()-[]{};:'",<>./?@#$%^&*_~''

### Full Capital: -

```python
if(fullcaps=="on"):
        analyzed=djtext.upper()
        '''for char in djtext:
            analyzed=analyzed+char.upper()'''
        params={'purpose':'Change to upper case', 'analyzed_text':analyzed}
        djtext=analyzed
```
Function uses direct "char.upper" which converts all character to upper case.

### New Line Remover: -

```python
if(newlineremover=="on"):
        analyzed=""
        for char in djtext:
            if char !="\n" and char!="\r":
                analyzed=analyzed+char
        params={'purpose':'New Line Removed', 'analyzed_text':analyzed}
        djtext=analyzed
```

Function runs through For loop and checks for new line, and combines the left out text.

### Extra Space Remover: -

```python
if(extraspaceremover=="on"):
        analyzed=""
        for index,char in enumerate(djtext):
            if not (djtext[index]==" " and djtext[index+1]==" "):
                analyzed=analyzed+char
        params={'purpose':'Extra space Removed', 'analyzed_text':analyzed}
        djtext=analyzed
```

Same as above it checks for spacce more than 1 and connects the left out.

### Character Count: -

```python 
if(charcount=="on"):
        lenght=len(djtext)
        params={'purpose':'Number of character', 'analyzed_text':lenght}
        djtext=analyzed
```

Characters include space also so python has functionality called "len" which is efficiently used.
This funcationality is used to have specific Character counts in some forms or else.

## How all functionality works together!

```python
    if(removepunc!="on" and fullcaps!="on" and newlineremover!="on" and extraspaceremover!="on" and charcount!="on"):
        return HttpResponse("Error")
    return render(request, 'analyze.html', params)
```

This if statement will work for specific inputs.

## Approach : -

* Simple Django application.
* Tried to make a web-application which works for dyanmic input.
* Simple logics for funcationality.
