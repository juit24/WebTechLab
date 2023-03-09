# XML Question Paper File

**Human:**
Write a question paper as an XML file (question.xml say). The DTD is given below:
&lt;!ELEMENT question-paper (question*)&gt;
&lt;!ELEMENT question (text, optionA, optionB, optionC, optionD, answer)&gt;
&lt;!ELEMENT text (#PCDATA)&gt;
&lt;!ELEMENT optionA (#PCDATA)&gt;
&lt;!ELEMENT optionB (#PCDATA)&gt;
&lt;!ELEMENT optionC (#PCDATA)&gt;
&lt;!ELEMENT optionD (#PCDATA)&gt;
&lt;!ELEMENT answer (#PCDATA)&gt;
&lt;!ATTLIST question no CDATA #REQUIRED&gt;
&lt;!ATTLIST answer value (optionA|optionB|optionC|optionD) #REQUIRED&gt;

***

**Assistant:**

Here's an example of an XML file that follows the DTD given above:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE question-paper SYSTEM "question.dtd">
<question-paper>
  <question no="1">
    <text>What is the capital of France?</text>
    <optionA>Paris</optionA>
    <optionB>Berlin</optionB>
    <optionC>London</optionC>
    <optionD>Rome</optionD>
    <answer value="optionA"/>
  </question>
  <question no="2">
    <text>Which planet is known as the Red Planet?</text>
    <optionA>Mars</optionA>
    <optionB>Venus</optionB>
    <optionC>Jupiter</optionC>
    <optionD>Saturn</optionD>
    <answer value="optionA"/>
  </question>
</question-paper>

```


***

**Human:**
will all the dtd content stored in question.dtd file?

***

**Assistant:**

Yes, the DTD content would typically be stored in a separate file, in this case named "question.dtd", and referenced in the XML file using a `DOCTYPE` declaration. For example:

```
<!DOCTYPE question-paper SYSTEM "question.dtd">

```

This specifies that the DTD for the document is stored in the "question.dtd" file. The SYSTEM keyword is used to indicate that the DTD is stored in a separate file, rather than being included inline within the XML document.


***

**Inline DTD**

```
<!DOCTYPE question-paper [
<!ELEMENT question-paper (question*)>
<!ELEMENT question (text, optionA, optionB, optionC, optionD, answer)>
<!ELEMENT text (#PCDATA)>
<!ELEMENT optionA (#PCDATA)>
<!ELEMENT optionB (#PCDATA)>
<!ELEMENT optionC (#PCDATA)>
<!ELEMENT optionD (#PCDATA)>
<!ELEMENT answer (#PCDATA)>
<!ATTLIST question no CDATA #REQUIRED>
<!ATTLIST answer value (optionA|optionB|optionC|optionD) #REQUIRED>
]>
<question-paper>
  <question no="1">
    <text>What is the capital of France?</text>
    <optionA>London</optionA>
    <optionB>Paris</optionB>
    <optionC>Moscow</optionC>
    <optionD>New York</optionD>
    <answer value="optionB">Paris</answer>
  </question>
  <question no="2">
    <text>Who invented telephone?</text>
    <optionA>Alexander Graham Bell</optionA>
    <optionB>Thomas Edison</optionB>
    <optionC>Nikola Tesla</optionC>
    <optionD>Michael Faraday</optionD>
    <answer value="optionA">Alexander Graham Bell</answer>
  </question>
  <question no="3">
    <text>What is the largest planet in our solar system?</text>
    <optionA>Venus</optionA>
    <optionB>Mars</optionB>
    <optionC>Earth</optionC>
    <optionD>Jupiter</optionD>
    <answer value="optionD">Jupiter</answer>
  </question>
</question-paper>

```

This can validated using https://www.xmlvalidation.com/
