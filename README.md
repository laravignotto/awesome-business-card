# Awesome Business Card

[Olivier Pieters' Business Card](https://github.com/opieters/business-card) inspired LaTeX template for business cards with [Byungjin Park's Awesome CV](https://github.com/posquit0/Awesome-CV) style.

---

<kbd>![business card example](https://github.com/laravignotto/awesome-business-card/blob/main/figures/business_card.png?raw=true)</kbd>

---

## Customizations

You can choose between the international business card size (55mm x 85mm) or the North America business card size (2in x 3.5in) by uncommenting the corresponding line at the beginning of the file. Default is internationa size.
```latex
% business card size (international)
\usepackage[paperwidth=55mm,paperheight=85mm,margin=0cm,noheadfoot]{geometry}
% business card size (North America)
% \usepackage[paperwidth=2in,paperheight=3.5in,margin=0cm,noheadfoot]{geometry}
```

You can define the color of the separation lines, icons, text, and job title. The default is red for the separation lines and job title, and a dark color for the icons and text.
```latex
\definecolor{seplinecolour}{HTML}{FB4485}  % separation lines
\definecolor{iconcolour}{HTML}{2F3142}     % icons
\definecolor{textcolour}{HTML}{2F3142}     % text
\definecolor{jobtitlecolour}{HTML}{FB4485} % job title
```

The business card is divided into three parts separated by lines. In the first section specify your name and job title.
```latex
    % name, surname, job title
    \matrix[every node/.style={anchor=center,font=\huge},anchor=center] (name) {
        \node{\namefont Name}; \\
        \node{\surnamefont\bfseries Surname}; \\
        \node{\color{jobtitlecolour}
            \footnotesize
            \sourcesanspro\scshape
            Job Title}; \\
    };
```

In the second section there are contact information. **Important:** if you add or remove lines from this section (default is 4 lines) you may have to adjust the figure width in the following section accordingly, to keep everything into the space of the card. You could also change the font size from `\small` to `\normalsize` or `\footnotesize`.
```latex
    % contact info
    \matrix [below=\seplinedistance of hl1,%
            column 1/.style={anchor=center,color=iconcolour},%
            column 2/.style={anchor=west}] (contact){
        % comment, uncomment or add nodes with info if needed
        % adjust figure width below if needed when adding/removing lines here
        \node{\faGlobe}; & \node{\small example.com};\\
        \node{\faEnvelope}; &\node{\small example@example.com};\\
        \node{\faMobile}; &\node{\small +1 555 0000}; \\
        \node{\faGithubSquare}; &\node{\small example}; \\
        % \node{\faLinkedinSquare}; &\node{\small example}; \\
    };
```

The third section loads an image. Could be a logo, or your photo, default is a qr code. You may have to adjust the figure width if you added or removed lines from the previous section. 
```latex
% image
    \node [below=\seplinedistance of hl2]
    % adjust width if needed
    {\includegraphics[width=.4\textwidth]{figures/qr-code.png}};
```
