# MEX #
While the repository may have files already MEX'd, it is strongly recommended that you compile your own files.

>Mathworks' reference to MEX'ing:
[http://bit.ly/141doGh](http://bit.ly/141doGh)

>Mathworks' reference to debugging a MEX file:
[http://bit.ly/18zBn2T](http://bit.ly/18zBn2T)

## Notes ##

- When debugging MEX files with Visual Studio, MEX debug symbols are loaded dynamically. This may cause an indication within the VS IDE that a breakpoint will not be hit. This often proves to be incorrect.
- There are dependencies between certain MEX files such that within a given MEX'd compilation an external function (or library) may be referenced. Using [numTicksProfit](https://github.com/mtompkins/openAlgo/tree/master/Matlab/MEX/Cpp/numTicksProfit "numTicksProfit") as an example, this routine relies on trivial functions that are located within [myMath.cpp](https://github.com/mtompkins/openAlgo/tree/master/Cpp/myFunctions "myMath.cpp").  The MEX command within Matlab then has the following form to include the external referenced file:

    `mex numTicksProfit.cpp -g G:\openAlgo\Cpp\myFunctions\myMath.cpp -IG:\openAlgo\Cpp\myFunctions`

	where '-IG:\openAlgo\...' is '*dash EYE somePath*' to indicate an Include as per Matlab documentation. Also shown is the '-g' option to create a symbol file for debugging.
- Included within the MEX section is the [taInvoke](https://github.com/mtompkins/openAlgo/tree/master/Matlab/MEX/Cpp/taInvoke) wrapper for the external C++ [ta-lib](http://www.ta-lib.org/) library. This allows calling many optimized C++ analytical functions from within Matlab.


Revision: 5780.25390
