gplot
=====

Use [gnuplot](http://www.gnuplot.info/) to plot one or more files directly from
the command line.  Originally discussed in the posting [Using gnuplot from the
command
line](http://agentzlerich.blogspot.com/2011/04/using-gnuplot-from-command-line.html)
but extended greatly from that initial appearance.

```
Usage: gplot [OPTION]... (FILE|EXTGLOB) GNUPLOTCMD...
Use gnuplot to plot one or more files directly from the command line.

  -3             Perform 3D plotting using gnuplot's splot command.
  -c             Populate the key using autotitling.
  -f FOREXPR     Prepend a 'for [FOREXPR]' to the plotting command.
  -g PATTERN     Grep for PATTERN in the input processing only matches.
  -h             Show this help message.
  -i             Interactive plotting mode.  Hit 'h' on plot for help.
  -l             Use logarithmic scale for y axis.
  -o FILE        Save the plot to FILE with type chosen via the extension.
                 Encapsulated postscript (eps), PNG, JPEG, and SVG supported.
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
  -S             Prior to plotting, read auxililary gnuplot from stdin.
  -X XLOW:XHIGH  Specify an explicit x axis range instead of autoscaling.
  -Y YLOW:YHIGH  Specify an explicit y axis range instead of autoscaling.
  -Z ZLOW:ZHIGH  Specify an explicit z axis range instead of autoscaling.

Examples (see gnuplot documentation for complete GNUPLOTCMD details):

  gplot -c -i foo.dat using 1:2 with linespoints
  gplot -s foo.gp -X 0:1 -Y 0:2 foo.dat using 1:2 with linespoints
  gplot -o foo.eps foo.dat using 1:2 with linespoints
  gplot -f i=2:5 -p foo.png foo.dat using 1:i with points
  gplot -3 restart\*.dat using '"x":"y":"z"'
  gplot -H 0.01 foo.dat using '(bin($1,bw)):(1.0)' smooth frequency with boxes
  gplot foo.dat using '9:(0.0001)' smooth kdensity

Input files compressed by bzip2, gzip, or xz are transparently decompressed.
Variable $GNUTERM, defaulting to "x11 enhanced", sets the gnuplot terminal.
On error, the failing gnuplot script is shown.
```
