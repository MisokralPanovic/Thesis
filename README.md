# Michal Varga PhD thesis

This repository contains the LaTeX source files and supporting materials for my PhD thesis, which was successfully defended at the University of Cambridge. It is based on [CUED PhD thesis template](https://github.com/kks32/phd-thesis-template) by Krishna Kumar. The project demonstrates my ability to:

- **Write in LaTeX:** I used LaTeX for the entire document creation process, showcasing my proficiency with the platform, particularly for managing complex academic documents.
- **Work with Large Documents:** The thesis, comprising multiple chapters, appendices, figures, tables, and references, highlights my ability to structure and organize extensive documents efficiently.
- **Academic/Medical Writing:** The content focuses on advanced topics in molecular pathology, pharmacology, and virology, evidencing my ability to communicate complex scientific research clearly and effectively.
- **File and Project Management:** This repository illustrates my ability to manage a large-scale writing project, including version control, organizing LaTeX files, and handling the compilation of a document with multiple components.

Example code from the **`Methods`** section:

```latex
\chapter{Materials and Methods} \label{ch:Materials and Methods}
\section{Cell Culture} \label{sec:Cell Culture}
\subsection{Cell Culture Conditions} \label{subsec:Cell Culture Conditions}
All cell lines, as outlined in Table \ref{tab:Cell Lines Table}, underwent cultivation in cell culture flasks (Corning) under standardised conditions: 37°C within a 5\% \ch{CO2} atmosphere. With the exception of BEAS2B, which followed a distinct protocol, all cell lines were sustained in complete Dulbecco’s modified Eagle's medium (DMEM; Sigma-Aldrich). This medium was fortified with 10\% foetal bovine serum (FBS, Sigma-Aldrich), 1\% L-glutamine (Sigma-Aldrich), and a 1\% penicillin and streptomycin mixture (TermoFisher). In contrast, the BEAS2B cell line adhered to a specialised regimen, being cultured in LHC basal medium (TermoFisher) supplemented with 10\% FBS (Sigma-Aldrich), 1\% L-glutamine (Sigma-Aldrich), and 1\% penicillin and streptomycin mixture (TermoFisher).

\begin{table}
  \centering
  \begin{tabular}{lll}
    \toprule
    {\textbf{Cell Line}} &
  {\textbf{Description}} &
  {\textbf{Source}} \\ \midrule
    Vero & Monkey Kidney Epithelial Cells & The Pirbright Institute \\ 
    A549 & Human Alveolar Epithelial Cancer Cells &  The Pirbright Institute \\
    HEK293T & Human Embryonic Kidney Cells & The Pirbright Institute \\ 
    MDBK & Madin-Darby Bovine Kidney Cells & The Pirbright Institute \\
    BT & Bovine Turbinate Epithelial Cells & The Pirbright Institute \\
    HeLa & Human Uterine Epithelial Cancer Cells & The Pirbright Institute \\
    BEAS2B & Human Bronchial Epithelial Cells & ATCC  \\ \bottomrule
  \end{tabular}
  \caption[Cell Lines Used in This Study.]{\textbf{Cell Lines Used in This Study.}}
  \label{tab:Cell Lines Table}
\end{table}

\subsection{Data Processing} \label{subsec:Data Processing}
Data processing, statistical analysis, and graph generation were conducted using the R programming language \cite{RCoreTeam2022R:Computing} within the RStudio environment \cite{RStudioTeam2022RStudio:RStudio}. Tidyverse and data.table R packages \cite{Wickham2019WelcomeTidyverse, Dowle2022Data.table:data.frame} were employed for data manipulation, while ggplot and scales R packages were utilised for plotting \cite{Wickham2019WelcomeTidyverse, Wickham2022Scales:Visualization}. For human \textit{IFIT} targets and bovine \textit{Mx1}, relative differences in transcript abundance between conditions were established using the $\Updelta$$\Updelta$ cycle threshold (Ct) methodology with internal calibrators (human and bovine \textit{GAPDH} respectively). The formulas can be seen in Figure \ref{eq:Mathematical Bases of delta delta Ct Relative Quantification Method}. The final values were divided by the mean control values to standardise the data. For custom-created bovine \textit{IFIT} primer pairs described in Section \ref{tab:Bovine IFIT qPCR Primers table}, the absolute amount of material detected was extrapolated from standard curves, calculated using the equation shown in Figure \ref{eq:Amplification Efficiency Equation}. The slope of the standard curves was also assessed to evaluate the best candidate primer pairs for subsequent experiments and as an internal control for batch variation. The internal calibrator (bovine \textit{GAPDH}) was run alongside the bovine \textit{IFIT} samples and used to factorise the extrapolated values in accordance with the differential abundance of the internal calibrator detected between conditions. In other words, the \(2^{-\Updelta\Updelta \mbox{Ct}}\) values from bovine \textit{GAPDH} of different conditions were divided by the value measured in control conditions. This vector of relative abundance between conditions was applied as a factor on measured bovine \textit{IFIT} extrapolated values, which were priorly modified into a vector of relative abundances standardised to control themselves. This was done to control for differential amplification efficiencies observed between different bovine \textit{IFIT} primer pairs. As each experiment was standardised to the control conditions, it was possible to aggregate data points from different experiments into one large dataset. Because control conditions always had a relative value of one, they were omitted from the graphs. All the other conditions are shown as relative abundance values to the control and to each other.

\begin{figure}
$$\mbox{Relative Quantification} = 2^{\Updelta\Updelta \mbox{Ct}}$$
$$\Updelta\Updelta \mbox{Ct} = \Updelta \mbox{Ct}_{\mbox{Test Samples}}-\Updelta \mbox{Ct}_{\mbox{Calibrator Samples}}$$
$$\Updelta \mbox{Ct}_{\mbox{Test Samples}} = \mbox{Ct}_{\mbox{Target Gene in Tests}}-\mbox{Ct}_{\mbox{Reference Gene in Tests}}$$
$$\Updelta \mbox{Ct}_{\mbox{Calibrator Samples}} = \mbox{Ct}_{\mbox{Target Gene in Calibrator}}-\mbox{Ct}_{\mbox{Reference Gene in Calibrator}}$$
\caption[Mathematical Basis of $\Updelta$$\Updelta$Ct Relative Quantification Method.]{\textbf{Mathematical Basis of $\Updelta$$\Updelta$Ct Relative Quantification Method.}}
\label{eq:Mathematical Bases of delta delta Ct Relative Quantification Method}
\end{figure}

\section{DNA Work} \label{sec:DNA Work}
\subsection{DNA Plasmids} \label{subsec:DNA Plasmids}
All plasmids used in this project had their backbone based on either SCRPSY or pcDNA3.1. Their schematics can be seen in Figure \ref{fig:SCRPSY Representative Map} and Figure \ref{fig:pcDNA3.1 Representative Map}, respectively. SCRPSY-backed plasmids were provided by CRV Glasgow and were part of their interferon-stimulated genes plasmid library. These included open reading frames (ORFs) of bovine \textit{IFIT1}, \textit{IFIT2}, \textit{IFIT3}, and \textit{IFIT5}, as well as human \textit{IFIT1B}, \textit{IFIT2}, \textit{IFIT3}, and \textit{IFIT5}. The ORFs in these constructs do not possess any tags. The benefit of the SCRPSY backbone is the possibility of delivery inside the cells by direct transfection or by transduction. SCRPSY plasmids containing bovine \textit{IFIT} ORFs were used as templates for the generation of tagged bovine \textit{IFITs} in pcDNA3.1 plasmid backbones. pcDNA3.1-backed plasmids with ORFs for human \textit{RSV P}, human \textit{RSV N}, human \textit{RSV N} conjugated to green fluorescent protein (GFP), bovine \textit{RSV P}, bovine \textit{RSV N}, bovine \textit{RSV N} conjugated to GFP, and \textit{GFP} conjugated to FLAG, human \textit{IFIT1} conjugated to FLAG, human \textit{IFIT2} conjugated to FLAG, and human \textit{IFIT5} conjugated to FLAG were provided by the Viral Glycoproteins Group and Viral Gene Expression Group (both from the Pirbright Institute) respectively.

\begin{figure}
    \centering
    \includegraphics[width=0.6\linewidth]{05. Methods/Figs/01. scrpsy.pdf}
    \caption[SCRPSY Representative Map.]{\textbf{SCRPSY Representative Map.}}
    \label{fig:SCRPSY Representative Map}
\end{figure}
```