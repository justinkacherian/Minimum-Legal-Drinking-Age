use "C:\Users\justi\OneDrive\Stata\Datasets\deaths.dta"
export excel using helloworld1.xls, firstrow(varlabels)


*no state trends and no weights
eststo est1: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 1, cluster(state)
eststo est2: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 2, cluster(state)
eststo est3: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 3, cluster(state)
eststo est4: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 6, cluster(state)

* state trends and no weights
eststo est5: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 1, cluster(state)
eststo est6: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 2, cluster(state)
eststo est7: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 3, cluster(state)
eststo est8: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 6, cluster(state)

* no state trends but weights included
eststo est9: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 1 [aw=pop], cluster(state)
eststo est10: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 2 [aw=pop], cluster(state)
eststo est11: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 3 [aw=pop], cluster(state)
eststo est12: reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 6 [aw=pop], cluster(state)

* weights and state trends
eststo est13: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 1 [aw=pop], cluster(state)
eststo est14: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 2 [aw=pop], cluster(state)
eststo est15: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 3 [aw=pop], cluster(state)
eststo est16: reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 6 [aw=pop], cluster(state)

esttab est using ols.rtf

preserve
sort year dtype
collapse mrate legal ,  by (year dtype state)
twoway line mrate year  if dtype == 2 & (state==6 | state == 36) ///
|| line legal year  , yaxis(2) title("Motor Vehicle Mortality & % 18-20 Allowed to Dringk")
restore

preserve
keep if agegr == 2 & dtype == 2
collapse mrate legal [aw=pop],  by (year dtype agegr) 
export excel using dataProjectQ1Q23.xls, firstrow(varlabels)
restore


preserve
keep if agegr == 2 & dtype == 2 & (state == 6 | state == 36)
collapse mrate legal,  by (year dtype agegr state) 
export excel using dataProjectQ3.xls, firstrow(varlabels)
restore

sum mrate by (year)

preserve
sort year dtype
collapse mrate legal 
line mrate year  if agegr == 2 & dtype == 2 ///
|| line legal year  , yaxis(2) title("Motor Vehicle Mortality & % 18-20 Allowed to Dringk")
restore

reg mrate legal if (dtype == 2 & (state == 6 | state == 36) & year >= 1982)
reg mrate legal i.state##c.year i.year if year >= 1988 & agegr == 2 & dtype == 2, cluster(state)

*no state trends and no weights
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 1, cluster(state)
scalar coef1 = _b[legal]
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 2, cluster(state)
scalar coef2 = _b[legal]
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 3, cluster(state)
scalar coef3 = _b[legal]
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 6, cluster(state)
scalar coef4 = _b[legal]

* state trends and no weights
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 1, cluster(state)
scalar coef5 = _b[legal]
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 2, cluster(state)
scalar coef6 = _b[legal]
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 3, cluster(state)
scalar coef7 = _b[legal]
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 6, cluster(state)
scalar coef8 = _b[legal]

* no state trends but weights included
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 1 [aw=pop], cluster(state)
scalar coef9 = _b[legal]
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 2 [aw=pop], cluster(state)
scalar coef10 = _b[legal]
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 3 [aw=pop], cluster(state)
scalar coef11 = _b[legal]
reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == 6 [aw=pop], cluster(state)
scalar coef12 = _b[legal]

* weights and state trends
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 1 [aw=pop], cluster(state)
scalar coef13 = _b[legal]
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 2 [aw=pop], cluster(state)
scalar coef14 = _b[legal]
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 3 [aw=pop], cluster(state)
scalar coef15 = _b[legal]
reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == 6 [aw=pop], cluster(state)
scalar coef16 = _b[legal]

#delimit;

matrix A = matuniform(4,6);
matrix A = (coef1,coef5,coef9,coef13)\(coef2,coef6,coef10,coef14)
\(coef3,coef7,coef11,coef15)\(coef4,coef8,coef12,coef16)\(0,1,0,1)\(0,0,1,1);

matrix rownames A = "All Deaths" "MV Accidents" "Suicide" "Internal" "State Trends" "Weights";
matrix colnames A = "(1)" "(2)" "(3)" "(4)";

esttab matrix(A,fmt("2 2 2 2 0 0")) using table5_2.rtf, title(MLDA Effects on Death Rates) 
addnotes("*For State Trends and Weights - 1 = Yes, 0 = No");



#delimit;

matrix A = matuniform(4,6);
matrix A = (coef1,coef5,coef9,coef13)\(coef2,coef6,coef10,coef14)
\(coef3,coef7,coef11,coef15)\(coef4,coef8,coef12,coef16)\(0,1,0,1)\(0,0,1,1);

matrix rownames A = "All Deaths" "MV Accidents" "Suicide" "Internal" "State Trends" "Weights";
matrix colnames A = "(1)" "(2)" "(3)" "(4)";

esttab matrix(A,fmt("2 2 2 2 0 0")) using table5_2.rtf, title(MLDA Effects on Death Rates) 
addnotes("For State Trends and Weights - 1 = Yes, 0 = No" "* p < 0.05, ** p < 0.01, *** p < 0.001");




* death cause: 1=all, 2=MVA, 3=suicide, 6=internal
foreach i in 1 2 3 6{


reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == `i', cluster(state)


reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == `i', cluster(state)



reg mrate legal i.state i.year if year <= 1983 & agegr == 2 & dtype == `i' [aw=pop], cluster(state)


reg mrate legal i.state##c.year i.year if year <= 1983 & agegr == 2 & dtype == `i' [aw=pop], cluster(state)
}
// */

esttab using yest.rtf, keep(legal) se(2)
