---
layout: post
title: Application Packages
date: 2010-12-03 15:54:36.000000000 -05:00
category: post
comments: true
image:
  teaser: https://i0.wp.com/farm6.static.flickr.com/5282/5229308197_b154d1ccae_m_d.jpg
---

The problem at hand is the following: a few months before graduation, a Ph.D. candidate usually sends hundreds of application packages to different universities, research institutions and companies, with the intention of gaining a profitable job.  We all agree that the process is certainly painful: gathering reference letters, writing one (or several) research statement, teaching philosophy, and original cover letters.  The aim is to make you stand out from the rest of candidates.

While I will not give you any hint on successful statement writing, or superb composition, I would like to show you how to accomplish the task of mass-producing a high-quality set of cover letters for all the jobs of your choice.  The final product will comprise several copies of letters that look something like this:

<p style="text-align:center;"><img style="border-style:solid;border-width:1px;" src="https://i0.wp.com/farm6.static.flickr.com/5001/5229347341_187da95520_o_d.jpg" alt="" width="60%" /></p>

Notice the structure of that letter: opening, a formal job request, short introduction, a big paragraph (where I may or may not include any text that makes the letter more personal), and finally a closing.  Note also the fact that the letter carries the official logo and footer of the University.  All this was accomplished directly in <span>\\( \LaTeX \\)</span>, without the need to purchase special paper, or signing personally each letter.

We start by gathering the proper logo online from the official pages of the University, and your signature.  For the latter, sign on a blank piece of paper with a bold pen (like a Sharpie), and take a photo of the signature:

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="text-align:center;vertical-align:middle;width:30%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5243/5229261925_d2be08c802_o_d.gif" alt="" width="100%" /></td>
<td style="text-align:center;vertical-align:middle;width:70%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5170/5229250599_dded6109cb_d.jpg" alt="" width="100%" /></td>
</tr>
</tbody>
</table>

Crop the signature from the photo, and by playing with exposure, saturation, contrast, brightness and color, manipulate it until it looks like a proper signature in black ink, over a perfectly white background:

<p style="text-align:center;"><img style="border-style:solid;border-width:1px;" src="https://i0.wp.com/farm6.static.flickr.com/5282/5229308197_b154d1ccae_m_d.jpg" alt="" /></p>

For the next step, you need four <span>\\( \TeX \\)</span> files:

* A **class style** defining the overall look of your letters,
* a **master file** that runs the process of creation of the documents,
* a **data-base** with the addresses and other particular information for each of the positions that you are applying, and
* a **cover letter form**, where you actually use your creativity and composition prowess, to make a point across.

The cover letter form contains several variable fields, that must be filled with the data from the data-base. Upon compilation of the master file, we put it all together to obtain a different cover letter for each of the positions.

Let us go over the four documents in detail:

* **Class style**: cover letter style for University of South Carolina, `sclet.cls`.  It places the logo in the top left corner, the words "Department of Mathematics" and "College of Arts and Science" in the top right corner, a footer at the bottom of the page consisting on a burgundy horizontal line, followed below by the contact information of the University of South Carolina.  It also indicates the margins of the document, possible font sizes, forces a justified alignment of paragraphs, etc.

{% highlight latex linenos %}
\DeclareOption*{\PassOptionsToClass{\CurrentOption}{letter}}

\def\@checkoptions#1#2{
  \edef\@curroptions{\@ptionlist{\@currname.\@currext}}
  \@tempswafalse
  \@tfor\@this:=#2\do{
    \@expandtwoargs\in@{,\@this,}{,\@curroptions,}
    \ifin@ \@tempswatrue \@break@tfor \fi}
  \let\@this\@empty
  \if@tempswa \else \PassOptionsToClass{#1}{letter}\fi
}

\@checkoptions{12pt}{{10pt}{11pt}{12pt}}
\PassOptionsToClass{letterpaper}{letter}
\ExecuteOptions{letterpaper,12pt,oneside,onecolumn,final}
\ProcessOptions\relax

\LoadClass{letter}
\usepackage{graphicx}
\usepackage{color}
\ProvidesClass{sclet}[2010/12/05 University of South Carolina letter class]

\setlength{\longindentation}{0pt}
\setlength\headheight{18\p@}
\setlength{\headsep}{.25in}
\setlength{\evensidemargin}{\oddsidemargin}
\font\helv=cmss12
\font\helvsmall=cmss9

\font\deptfont=pplr at 10truept
\font\headfont=pplr at 10truept
\definecolor{burgundy}{rgb}{0.50196,0,0.12549} 
\addtolength{\topmargin}{-0.5pc}
\addtolength{\oddsidemargin}{-3pc}
\addtolength{\textwidth}{5.75in}

\newif\ifcolorlogo \newcommand{\ColorLogo}{\colorlogotrue}
\newcommand*{\fax}[1]{\def\faxnum{#1}}
\newcommand*{\email}[1]{\def\emailaddr{#1}}
\newcommand*{\url}[1]{\def\urladdr{#1}}
\newcommand{\deptname}{\headfont {\sc Department of Mathematics}}
\newcommand{\schoolname}{\headfont {\sc College of Arts and Sciences}}
\newcommand{\deptfoot}{\deptfont{\ifcolorlogo\color{burgundy}\fi\hrulefill}
  \\ \raisebox{-1ex}{University of South Carolina
    $\bullet$ Columbia, South Carolina 29208  $\bullet$ \telephonenum\
    $\bullet$ Fax: \faxnum } }
\renewcommand*{\opening}[1]{\ifx\@empty\fromaddress
  \thispagestyle{empty}
    {\relax}
  \else  
    \thispagestyle{empty}
    {\makebox[2.417in]{}\begin{tabular}{l@{}}\ignorespaces
      \fromaddress\end{tabular}\par}
  \fi
  \vspace{2\parskip}
  {\raggedright \toname \\ \toaddress \par}
  \vspace{2\parskip}
  #1\par\nobreak}
\renewcommand{\ps@empty}{
   \renewcommand{\@oddhead}{
        \vbox{
           \ifcolorlogo
             \vskip-0.406in{
               \includegraphics[width=2.078125in]{usc_logo}
             }
           \else
             \vskip-1.420in\hskip-1.092in{
               \includegraphics[width=5.5cm]{usc_logo}
             }
           \fi
           \ifcase \@ptsize\relax
             \hskip1.9in{\deptname}
           \or
             \hskip1.9in{\deptname}
           \or
             \hskip1.9in{\deptname}
           \fi
           \ifcase \@ptsize\relax
             \flushright{\schoolname}
           \or
             \flushright{\schoolname}
           \or
             \flushright{\schoolname}
           \fi
        }
   }
   \renewcommand{\@oddfoot}{
        \vbox{
           \ifcase \@ptsize\relax
             \vskip1.263in\hskip-0.027in{\deptfoot}
           \or
             \vskip1.388in\hskip-0.027in{\deptfoot}
           \or
             \vskip1.290in\hskip-0.040in{\deptfoot}
           \fi
        }
   }
}

\telephone{803/ 777-4224}
\fax{803/ 777-3783}
\email{use@math.sc.edu}
\url{http://www.math.sc.edu}
{% endhighlight %}

* **Master file**: It could not be simpler.

{% highlight latex linenos %}
\documentclass[10pt]{sclet}

\signature{\vskip-0.6in{\includegraphics[width=5.55cm]{signature.jpg}}\\
Francisco Javier Blanco-Silva\\
My address\\
City, State, zip code}
\textwidth = 6.25in
\textheight = 8.5in
\ColorLogo

\begin{document}
\input cov.tex      
\input Addr.tex     
\end{document}
{% endhighlight %}

* **Database**: The variable `\cov` is defined, as an entity with several fields (say 5 for the purposes of this example).  The first entry is the address of the position, the second entry is the opening of the letter, the third entry is the name of the company/department, and finally the fifth entry is an optional paragraph.  The collection of all possible positions is stored in the file `Addr.tex`, that looks something like this:

{% highlight latex linenos %}
\cov{     
Hiring Committee\\
Department of Mathematics\\
School of Life\\
Springflied, ST  50505
}
{Dear Professors:}
{postdoctoral associate/part-time instructor positions}
{the Department of Mathematics of the School of Life.}
{
Romani ad multas terras navigant aut ambulant. Saepe Romani in Europa
terras occupant. Hae terrae tum sunt provinciae Romae. Prima provincia
Romae erat Sicilia. Sicilia est insula. Multa aqua est circum Siciliam.
Romani ad Siciliam navigant et terram occupant. In Sicilia sunt multi
agricolae,et agricolae Siciliae Romanis cibum et praedam donant Provincia
Hispaniae est paeninsula. Provincia Hispaniae ad Romanos cibum et praedam
portat. Iulius Caesar Romanis fabulas pugnarum in Gallia in Commentarii
de Bello Gallico narrat. Etiam Caesar ad Britanniam navigat et pugnat, sed
tum Britannia non est provincia. Postea, imperator Claudius ad Brittaniam
navigat et Romanis terram mandat. Etiam Romania est provincia Romana.
Romani Romaniam provinciam Daciam appellant. Romani, vias et fora in
provinciis aedificant. Etiam provinciis linguam Latinam mandant.  In
provinciis Hispaniae, Galliae et Romaniae hodie linguae sunt "Linguae
Romanae".
}

\cov{ ...  
{% endhighlight %}

* **Cover letter form**:  The file `cov.tex`, where we define the entity `\cov`, and start a letter in the usual <span>\\( \LaTeX \\)</span> way.

{% highlight latex linenos %}
\newcommand{\cov}[5]
{
\begin{letter}{#1}
\opening{#2}

[First paragraph, declaration of intentions]
This letter is in regards to the formal submission of my application
for the {#3} currently open at {#4}

[Second paragraph, introduction of myself and my work.]
I completed my doctorate in [...] and many questions remain open.

[Third paragraph, I sell myself a little]
I have a very ample experience in teaching: I have had the opportunity
[...] All these are also available at \url{blancosilva.wordpress.com}

[Fourth paragraph, I get a little personal.]
{#5}

[And closing.  Give contact info.]
I look forward to discussing the qualifications for the position
further. [...] Thank you for your consideration.

\closing{Sincerely,}
\deptfoot
\end{letter}
}
{% endhighlight %}
