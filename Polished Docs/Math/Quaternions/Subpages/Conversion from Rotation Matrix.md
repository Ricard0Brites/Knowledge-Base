# Quaternion Conversion from Rotation Matrix (Right-Handed)

Given a 3x3 rotation matrix:

$$ 
R =
\begin{bmatrix}
    R_{00} & R_{01} & R_{02} \\
    R_{10} & R_{11} & R_{12} \\
    R_{20} & R_{21} & R_{22}
\end{bmatrix}
$$ 

The quaternion components can be calculated as follows:

1.  Calculate the trace: $tr = R_{00} + R_{11} + R_{22}$
2.  If $tr > 0$:
    $S = \sqrt{tr + 1.0} \times 2$
    $w = 0.25 \times S$
    $x = (R_{21} - R_{12}) / S$
    $y = (R_{02} - R_{20}) / S$
    $z = (R_{10} - R_{01}) / S$
    ---
3.  Else if $R_{00} > R_{11}$ and $R_{00} > R_{22}$:
    $S = \sqrt{1.0 + R_{00} - R_{11} - R_{22}} \times 2$
    $w = (R_{21} - R_{12}) / S$
    $x = 0.25 \times S$
    $y = (R_{01} + R_{10}) / S$
    $z = (R_{02} + R_{20}) / S$
    ---
4.  Else if $R_{11} > R_{22}$:
    $S = \sqrt{1.0 + R_{11} - R_{00} - R_{22}} \times 2$
    $w = (R_{02} - R_{20}) / S$
    $x = (R_{01} + R_{10}) / S$
    $y = 0.25 \times S$
    $z = (R_{12} + R_{21}) / S$
    ---
5.  Else:
    $S = \sqrt{1.0 + R_{22} - R_{00} - R_{11}} \times 2$
    $w = (R_{10} - R_{01}) / S$
    $x = (R_{02} + R_{20}) / S$
    $y = (R_{12} + R_{21}) / S$
    $z = 0.25 \times S$

Remember to normalize the resulting quaternion to ensure it is a unit quaternion.
