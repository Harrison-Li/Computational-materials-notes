# Sequence model

## RNN

### Notations

X is input, Y is output tells you for each part of input words is that part of a person's name.

**X:** Harry Potter and Hermione Granger invented a new spell.

​     $x^{<1>},x^{<2>},x^{<3>}....x^{<t>}...x^{<9>} \longrightarrow\quad T_x=9$

**Y:**      1       1	 0	    1	        1   	    0	0    0     0

​	$y^{<1>},y^{<2>},y^{<3>}....y^{<t>}...y^{<9>} \longrightarrow\quad T_y=9$

- $T_x,T_y$ denote the length of the sequence.
- $x^{(i)<t>}$ the TIF element is the sequence of training example i.
- $T_y^{(i)}$ is the length of output sequence in the i training example.

**Representing words **

<u>Vocabulary</u>

$\left[ \begin{matrix}   a \\   apron \\ .\\.\\.\\and\\.\\.\\.\\harry\\.\\.\\.\\potter \\.\\.\\.\\zulu \end{matrix}  \right] $  $\rightarrow$$\begin{matrix}   1  \\   2 \\ .\\.\\.\\  367\\.\\.\\.\\4075\\.\\.\\.\\ 6830\\.\\.\\.\\10,000\end{matrix}$  			$x^{<1>}\rightarrow y^{<1>}=\left[ \begin{matrix}   0 \\   0 \\ .\\.\\.\\0\\.\\.\\.\\1\\.\\.\\.\\0 \\.\\.\\.\\0 \end{matrix}  \right] $$\uparrow\\ \\\\\\\\10,000\\\\\\\\ \downarrow$

​											    One-hot

### Recurrent Neural Network Model

