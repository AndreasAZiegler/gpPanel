gpPanel -- Easy Chart panel for wxWidget

URL: http://code.google.com/p/gppanel/

gpPanel is chart libary for wxWidget. It inheritance from wxPanel and
use modified [wxMathPlot](http://wxmathplot.sourceforge.net/) library
at chart engine. Flexible to use and easy to implement new gpLayers
from examples.

Adapted gpPanel to be capable of dealing with real time data. For this I replaced the std::vector with a std::deque and added the funcitionality that only the newest data point are kept.
