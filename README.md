gplot
=====

Use [gnuplot](http://www.gnuplot.info/) to plot one or more files directly from
the command line.  Originally discussed in the posting [Using gnuplot from the
command
line](http://agentzlerich.blogspot.com/2011/04/using-gnuplot-from-command-line.html)
but extended greatly from that initial appearance.

```
Usage: gplot [OPTION]... [GNUPLOTSPEC...] [::: [FILE]...]
Use gnuplot to plot one or more files directly from the command line.

  -3             Perform 3D plotting using gnuplot's splot command.
  -c             Populate the key using autotitling.
  -e             Turn on enhanced terminal features.
  -f FOREXPR     Prepend a 'for [FOREXPR]' to the plotting command.
  -g PATTERN     Grep for PATTERN in the input processing only matches.
  -h             Show this help message.
  -i             Interactive plotting mode.  Hit 'h' on plot for help.
  -l             Use logarithmic scale for y axis.
  -o FILE        Save the plot to FILE with type chosen via the extension.
                 Formats EPS, JPEG, PDF, PNG, and SVG supported.
  -s FILE        Save the generated gnuplot commands as a script called FILE.
  -t TITLE       Set TITLE as the plot title.
  -x XLABEL      Specify XLABEL as the x axis label.
  -y YLABEL      Specify YLABEL as the y axis label.
  -z ZLABEL      Specify ZLABEL as the z axis label.
  -C             Process comma-separated value (CSV) data.
  -F FREQUENCY   Replot the inputs every FREQUENCY seconds.
  -G             Show grid lines.
  -H BW          Ease making histograms using binwidth BW; see examples.
  -L             Use logarithmic scale for x axis.
  -M             In conjunction with option -3, employ 'set pm3d map'.
  -S FILE        Append the generated gnuplot commands to some FILE.
  -X XLOW:XHIGH  Specify an explicit x axis range instead of autoscaling.
  -Y YLOW:YHIGH  Specify an explicit y axis range instead of autoscaling.
  -Z ZLOW:ZHIGH  Specify an explicit z axis range instead of autoscaling.

Examples (see gnuplot documentation for complete GNUPLOTSPEC details):

  gplot -eci using 1:2 with linespoints ::: foo.dat
  gplot -s foo.gp -X 0:1 -Y 0:2 using 1:2 with linespoints ::: foo.dat
  gplot -c -o foo.eps using 1:2 with linespoints ::: <(head foo.dat | tail)
  gplot -f i=2:5 -o foo.png using 1:i with points ::: foo.dat
  gplot -3 using '"x":"y":"z"' ::: restart*.dat  # Escaping of column names...
  gplot -3 using x:y:z ::: restart*.dat          # ...is done automatically
  gplot -H 0.01 using '(bin($1,bw)):(1.0)' smooth frequency w boxes ::: foo.dat
  ls -rt | head | gplot using '9:(0.0001)' smooth kdensity

If [::: [FILE]...] is omitted, filenames are read from standard input.
Input files compressed by bzip2, gzip, or xz are transparently decompressed.
Variable $GNUTERM, defaulting to "wxt" then "x11", sets the default terminal.
On error, the failing gnuplot script is shown.
```
