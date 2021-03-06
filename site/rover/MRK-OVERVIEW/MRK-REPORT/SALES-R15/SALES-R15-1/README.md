##  Sales by Customer by Part (SALES.R15)

<PageHeader />

##

![](./SALES-R15-1.jpg)

**Job ID** Enter a unique ID if you wish to enter and save the parameters to
this procedure for future use. If you only need to run the procedure and do
not want to save your entry then you may leave this field empty.  
  
**Destination** Select the destination for the output from this procedure.  
  
**Process** Select the method to be used for processing the report. Foreground
is always available and must be used when output is directed to anything other
than a system printer (i.e. printers spooled through the database on the host
computer.) Depending on your setup there may be various batch process queues
available in the list that allow you to submit the job for processing in the
background or at a predefined time such as overnight. A system printer must be
specified when using these queues.  
  
**Format** Select the format for the output. The availability of other formats
depends on what is allowed by each procedure. Possible formats include Text,
Excel, Word, PDF, HTML, Comma delimited and Tab delimited.  
  
**Layout** You may indicate the layout of the printed page by specifying the
appropriate setting in this field. Set the value to Portrait if the page is to
be oriented with the shorter dimension (usually 8.5 inches) at the top or
Landscape if the longer dimension (usually 11 inches) is to be at the top.
Portrait will always be available but Landscape is dependent on the output
destination and may not be available in all cases.  
  
**Copies** Enter the number of copies to be printed.  
  
**Run Process** Click on the button to run the process. This performs the save
function which may also be activated by clicking the save button in the tool
bar or pressing the F9 key or Ctrl+S.  
  
**Start Date** Enter the range start date within which the shipment date must
fall to be selected for this report.  
  
**End Date** Enter the end range date within which the shipment date must fall
to be selected for this report.  
  
**Print Full Description** If this option is selected, the first 700
characters of the part will print on the report. This option is usually
selected when exporting the data to Excel or the gird viewer. If this option
is not selected only the first line of description will print on the report.  
  
**Exclude Totals** Check this box if you do not wish to print the total lines
on the report. This option is usually selected when sending the report to
Excel or the grid viewer.  
  
**Category** Enter the part categories you wish to include in this report. If
left blank, all categories will be included.  
  
**Customer/Price Code**  
  
**Co Code** Enter the company codes you wish to appear on this report. If left
blank all company codes will be included.  
  
**Customer Number** If you only want to list the shipments for a particular
customer then enter the customer number in this field. To include all
customers leave the field blank. If you do not know the customer number, there
is an option in the help menu for this prompt which allows you to select the
customer by name.  
  
**Name** Contains the name of the customer number entered. It may not be
changed.  
  
**Part Number** If you wish to run this report for specific parts, enter the
part numbers in thsi field. Leave this field blank to run the report for all
parts.  
  
**Pat Description** This field contains the first line of description for the
associated part number.  
  
**Last Status Message** Contains the last status message generated by the
program.  
  
**Last Status Date** The date on which the last status message was generated.  
  
**Last Status Time** The time at which the last status message was generated.  
  
  
<badge text= "Version 8.10.57" vertical="middle" />

<PageFooter />