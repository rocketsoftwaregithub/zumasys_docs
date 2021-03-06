##  Executive Business Inquiry (EXEC.Q)

<PageHeader />

**Form Details**  
[ Summary Chart ](EXEC-Q-1/README.md)   
[ Summary Data ](EXEC-Q-2/README.md)   
[ Cash ](EXEC-Q-3/README.md)   
[ Sales ](EXEC-Q-4/README.md)   
[ Customers ](EXEC-Q-5/README.md)   
[ Reps ](EXEC-Q-6/README.md)   
[ Receivables ](EXEC-Q-7/README.md)   
[ Purchasing ](EXEC-Q-8/README.md)   
[ Vendors ](EXEC-Q-9/README.md)   
[ Payables ](EXEC-Q-10/README.md)   
[ Inventory ](EXEC-Q-11/README.md)   
[ Production ](EXEC-Q-12/README.md)   

**Purpose**  
The EXEC.Q procedure provides an inquiry of a variety of financial and
business control figures. The intent is to provide the business executive with
a fast-access, concise look at the status of the company. All available
information is generated by date, normally on a nightly basis. The user may
enter any date for which information has been generated. Further, the user may
change the projected Accounts Receivable and projected Accounts Payable
figures in order to perform 'what-if' scenarios. Each change will show how
project cash flow will be affected.  
  
The Mtd/Ytd averages are a calculation of the monthly/yearly total divided by
the number of days within the month/year on which bookings/receipts/sales,
etc. actually occurred. For example, sales orders were only entered during the
month on 10 business days for a total of 12,000.00. The daily month-to-date
average would be = 12,000.00 / 10 days not 12,000.00 / 30 days  
  
The data that appears in this screen is generated by running the [ EXEC.P1 ](EXEC-P1/README.md) process for a specific date. Please note that if not all entries for a given day have been processed before [ EXEC.P1 ](EXEC-P1/README.md) runs, the totals showing in EXEC.Q will not reflect all the days work and may not reconcile to certain reports unless [ EXEC.P1 ](EXEC-P1/README.md) is re-processed for the day. If, for example, shipments are posted on 6/2/2010 for shipments that were sent on 6/1/2010, the shipment amounts showing in EXEC.Q will be under-stated unless [ EXEC.P1 ](EXEC-P1/README.md) is re-processed for June 1st. 

**Frequency of Use**  
As required.

**Prerequisites**  
The [ EXEC.P1 ](EXEC-P1/README.md) procedure must have been run for the date selected. Typically, [ EXEC.P1 ](EXEC-P1/README.md) is included in a batch routine that has been scheduled to run in the evening after most of the work for the day has been performed. 

<badge text= "Version 8.10.57" vertical="middle" />

<PageFooter />