

big_value comparison = how does 1 period compare with the one before it
a type of component

can give it the comparison period either through A, the date_range attr or B, as a calendar indirectly listed in filters=[...]

the bug happens when it is calculating the the previous period. it checks whether comparison has date_range nad only then sets the count attr which is used to shift the range back. for A it is fine for B there is no count so the shift is 0 and doesnt shift a