# WordSquareReferences
Enabling square references in bibliografy for Word.

By default Word surrounds citations by the round brackets, fortunately you can change it by aditing configuration file and change the citation type to square brackets or any other symbols. 

This is usefull if you are working on research papers and want to include references by using citation type links.

By default the style files are located in:
C:\Users\\{user_name}\AppData\Roaming\Microsoft\Bibliography\Style

1. open that folder and file: ISO690Nmerical.XSL in notepad
2. find the following part:

```
  <xsl:template name="templ_prop_OpenBracket" >
    <xsl:param name="LCID" />
    <xsl:variable name="_LCID">
      <xsl:call-template name="localLCID">
        <xsl:with-param name="LCID" select="$LCID"/>
      </xsl:call-template>
    </xsl:variable>
    <xsl:value-of select="/*/b:Locals/b:Local[@LCID=$_LCID]/b:General/b:OpenBracket"/>
  </xsl:template>

  
  <xsl:template name="templ_prop_CloseBracket" >
    <xsl:param name="LCID" />
    <xsl:variable name="_LCID">
      <xsl:call-template name="localLCID">
        <xsl:with-param name="LCID" select="$LCID"/>
      </xsl:call-template>
    </xsl:variable>
    <xsl:value-of select="/*/b:Locals/b:Local[@LCID=$_LCID]/b:General/b:CloseBracket"/>
  </xsl:template>
```  
3. change it to:
```
  <xsl:template name="templ_prop_OpenBracket" >
    <xsl:param name="LCID" />
    <xsl:variable name="_LCID">
      <xsl:call-template name="localLCID">
        <xsl:with-param name="LCID" select="$LCID"/>
      </xsl:call-template>
    </xsl:variable>
    <xsl:value-of select="/*/b:Locals/b:Local[@LCID=INITIAL_CONTENTLCID]/b:General/b:OpenBracket"/>
	<xsl:text>[</xsl:text>
  </xsl:template>

  
  <xsl:template name="templ_prop_CloseBracket" >
    <xsl:param name="LCID" />
    <xsl:variable name="_LCID">
      <xsl:call-template name="localLCID">
        <xsl:with-param name="LCID" select="$LCID"/>
      </xsl:call-template>
    </xsl:variable>
    <xsl:value-of select="/*/b:Locals/b:Local[@LCID=INITIAL_CONTENTLCID]/b:General/b:CloseBracket"/>
	<xsl:text>]</xsl:text>
  </xsl:template>
  ```
  or simply replace the file with file from repository (make a backup 1st)
  
  After changes are saved you can use the new reference scheme bu upadating existing fields or simply inserting new citation from References menu

