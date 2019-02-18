# interaction

*Change directory
cd "C:\Users\tbc\Desktop\PhD Sociology\Soc 710 - Research methods\assignement"

set more off

*read data
use sei_sample, clear

*Describe data

describe

browse

tab sex *Change directory
cd "C:\Users\tbc\Desktop\PhD Sociology\Soc 710 - Research methods\assignement"

set more off

*read data
use sei_sample, clear

*Describe data

describe

browse

tab sex 

*Generating missing values to create female where male takes value of 0 and female =1. 
gen female=.
replace female=0 if sex==1 
replace female=1 if sex==2 

*regression of seius age female and interaction between age and female
reg seius female c.age i.female#c.age
reg seius i.female##c.age

twoway (scatter seius age, msym(oh) jitter(3)) (lfit seius age if ~female) (lfit seius age if female), legend(order(2 "male" 3 "female"))

margins female

margins, at(age=(20(10)60))

margins female, at(age=(20(10)60))

margins, dydx(female) at(age=(20(10)60))

marginsplot, recast(line) recastci(rarea) yline(0)











*Generating missing values to create female where male takes value of 0 and female =1. 
gen female=.
replace female=0 if sex==1 
replace female=1 if sex==2 

*regression of seius age female and interaction between age and female
reg seius female c.age i.female#c.age
reg seius i.female##c.age

twoway (scatter seius age, msym(oh) jitter(3)) (lfit seius age if ~female) (lfit seius age if female), legend(order(2 "male" 3 "female"))

margins female

margins, at(age=(20(10)60))

margins female, at(age=(20(10)60))

margins, dydx(female) at(age=(20(10)60))

marginsplot, recast(line) recastci(rarea) yline(0)









