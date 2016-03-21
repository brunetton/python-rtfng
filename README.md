## Basic examples

### Hello World

```python
from rtfng.Elements import Document, Section

doc = Document()
section = Section()
section.append('Hello world !')
doc.Sections.append(section)

doc.write(file('hello.rtf', 'w'))
```

### Example 1

```python
from rtfng.Elements import Document, Section
from rtfng.document.paragraph import Paragraph
from rtfng.document.character import TEXT

# Init
doc = Document()
section = Section()

# First paragraph
p = Paragraph()
p.append('It is also possible to manully override a style:',
          TEXT(' this is a change of the font size', size=48),
         '.')
section.append(p)

# Empty paragraph
section.append('')

# Second paragraph
p = Paragraph()
p.append('This is a ',
          TEXT('very important information !', colour=doc.StyleSheet.Colours.Red, underline=True, bold=True)
        )
# Have a look to TEXT() definition in rtfng/document/character.py for more options

section.append(p)
doc.Sections.append(section)

doc.write(file('example.rtf', 'w'))
```

## Tests

For example usage, see the code in the unit tests in the 'test' directory and its subdirectories.

To run all tests:

    python test/test_all.py
    python test/test_doctests.py
