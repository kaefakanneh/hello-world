#Monmouth Telecom Billing 
## Table of Contents

1. [Kickoff Overnight Run]()
  - [x] What is the Overnight Run?
  - [ ] How to kick it off?
  - [ ] What machines are the **scripts** on?

2. [Raw2Sorted (Raw CDR's to Sorted)]()
  - [ ] What is **Raw2Sorted**?
  - [ ] Are there any **scripts** to run to ensure the process?
  - [ ] Where are the **scripts** located

3. [Sorted2Ccall (updates Caller Id and Ccall tables)]()
  - [ ] What is **Sorted2Ccall**?
  - [ ] At what point during the [billing process]() does this come into focus?
  - [ ] What machine is it on?

4. [Invoice Sanity Checker]()
  - [ ] What is **Invoice Sanity Checker**?
  - [ ] At what phase of the [billing process]() does it come into focus?
  - [ ] What machine is it on?

5. [Compute Phone Bill]()
  - [ ] What is **Compute Phone Bill**?
  - [ ] How and when do you **RUN** it?
  - [ ] What machine is it on?

6. [Trunk Utilization (Single Customer!!)]()
  - [ ] What is **Trunk Utilization**?
  - [ ] How and When do you **RUN** it?
  - [ ] What Machine and Directory is it under?

7. [Glossary]()
  - [ ] **CDR**: Call Data Records
  - [ ] **Old**: Processed CDR's
  - [ ] **New**: CDR's Waiting to be processed
  - [ ] **Sun Servers**: Serves as transit storage depot/station for CDR's en route to **Dadmin**.
  - [ ] **Switches**: Connect calls to intended destinations; create and transfer CDR's to Dadmin via Sun Servers. 
  
   |Switch Name | Numerical  Representation|
   |:-------------|:------------------------:|
   |Red Bank| 4 |
   |Camden| 5 |
   |Pleasantville| 6 |
   
  - [ ] **Processor 0**: **Red Bank** Switch
  - [ ] **Processor 1**: **Pleasantville** and Camden Switches

***

**SCRIPTS:**

checks for duplicate phone calls that are being billed (**No double billing same phone calls**):

``` bash
$ ./dup_calls.pl -y YYYY -m MM -s START_DATE -t END_DATE > /tmp/results
```

checks whether there are duplicate CNAME (**Caller ID services**):

``` bash
$ ./cname_dupe.pl -y YYYY -m MM > /tmp/cresults
```

checks:

``` bash
$ ./hpbx_hold.pl 

$ ./dump_invoice_holds > db_dumps/invoice_hold_YYYYMMDD.old

$ ./dump_invoice_holds > db_dumps/invoice_hold_YYYYMMDD.new

$ cd /dumps

$ diff *.old *.new
```

checks whether there are duplicate CNAME (**Caller ID services**):

``` bash
$ ./cname_dupe.pl -y YYYY -m MM > /tmp/cresults
```

<!-- Text comment -->
