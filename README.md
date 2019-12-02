
% =========================================================================================
% Template - Trabalho de Lógica 
%   
%   (sim, eu sei que você gostou do Chama na capa)
%
%   Os comentários que começam com '>' dizem basicamente o q vc tem q fazer;
%   A parte a ser editada começa depois de um 'EDITE A PARTIR DAQUI', antes
%   são as bibliotecas e funções
%
%   Passos para fazer um projeto editável com base nesse:
%   1. Crie uma conta e um projeto no overleaf
%   2. Nesse projeto aqui, clique em menu->source e baixe o zip
%   3. Dê upload nos arquivos desse zip no seu projeto
%
%   Se tiver interesse, pode ver como as funções são implementadas e tentar
%   fazer você mesmo :D
%
%   Autores: Franco Barpp Gomes              (https://github.com/Hyodar)
%            Lucas Eduardo Bonancio Skora    (https://github.com/LucasEBSkora)
%            Thiago de Mendonça Mildemberger (https://github.com/tmildemberger)
%            (turma 2019/1)
%
%   Se tiver alguma dúvida, pode procurar a gnt, mas acho que tá tudo explicado
%   suficientemente
%
% =========================================================================================

\documentclass[12pt]{article}

% Pacotes
% -----------------------------------------------------------------------------------------

 % encoding utf-8
\usepackage[utf8]{inputenc}

 % fica com os textos padrão em português
\usepackage[portuguese]{babel}

 % tabelas
\usepackage{tabularx}

 % indenta na primeira linha do parágrafo
\usepackage{indentfirst}

% background e scaling
\usepackage{tikz}
\usepackage{graphicx}

% pra usar espaçamentos de linha diferentes em cada parte do documento
\usepackage{setspace} 

% formatação das colunas do tabularx
\newcolumntype{s}{>{\hsize=.2\hsize\centering\arraybackslash}X}
\newcolumntype{b}{>{\hsize=.8\hsize\centering\arraybackslash}X}
\renewcommand{\tabularxcolumn}[1]{m{#1}}

% Comandos
% -----------------------------------------------------------------------------------------
% > mais abaixo no documento existem diversos exemplos de uso das funções abaixo

% \frase -> gera as tabelas de frase, formula e predicados/funcoes
% uso: \frase{predicados_funcoes}{frase}{formula}
\newcommand{\frase}[3]{
    \medskip
    \begin{center}
        \begin{tabularx}{\textwidth}{@{}|s|b|@{}}
          \hline
          Frase & #2 \\ \hline
          Fórmula & #3 \\ \hline
          Definições de predicados/funções & #1 \\ \hline
        \end{tabularx}
    \end{center}
}

% \const -> coloca o texto de um valor constante e atribui um nome de variável a ele
% uso: \const{valor_da_constante}
\newcounter{const}
\newcommand{\const}[1]{
    \protect\stepcounter{const}
    \q{#1}$^{\mathcal{M}_\themodelo}$ = vc\theconst
}

% \func -> coloca o texto de uma funcao
% uso: \func{nome_da_funcao}{valores_constantes_sep_por_virgula}{saidas_sep_por_virgula}
\newcounter{modelo}
\newcommand{\func}[3]{
    #1$^{\mathcal{M}_\themodelo}$(#2) = #3
}

% \pred -> coloca o texto de um predicado
% uso: \pred{nome_do_predicado}{constantes_afetadas_sep_por_virgula}
\newcommand{\pred}[2]{
    #1$^{\mathcal{M}_\themodelo}$ = \{#2\}
}

% \q -> coloca aspas no texto (quotes)
% uso: \q{texto}
\newcommand{\q}[1]{``#1''}

% \novoModelo -> aumenta a numeração do modelo
% uso: \novoModelo
\newcommand{\novoModelo}{
    \setcounter{const}{0}
    \protect\stepcounter{modelo}
}

% \conj -> insere um conjunto
% uso: \conj{nome_do_conjunto}{conteudo_sep_por_virgula}
\newcommand{\conj}[2]{
    #1 = \{#2\}
    \medskip
}

% =========================================================================================
% EDITE A PARTIR DAQUI
% =========================================================================================

% > coloque seu título dentro da tag \title{}
% > coloque os autores, separados como abaixo, e também dá de colocar os RAs

% Parâmetros do título
% -----------------------------------------------------------------------------------------

\title{Engenharia de Computação UTFPR}
\author{
        Luca Nozzoli (RA 2138085)
    \and
    \and
    \and
}
\date{\today}

% -----------------------------------------------------------------------------------------

% > se quiser, pode colocar um plano de fundo na capa, substituindo a imagem bg.png por uma imagem A4
% > se não quiser, exclua bg.png na coluna ao lado
% > (também pode ajustar a opacidade em 'opacity=')

% Titulo
% -----------------------------------------------------------------------------------------

\IfFileExists{}{
    \usepackage[firstpage]{draftwatermark}
    \SetWatermarkText{\tikz{\node[opacity=0.6]{\includegraphics[angle=-45]{bg.png}}}}
}{}

\begin{document}
\maketitle
\vfill 
 
\begin{center}
Trabalho de Representação de Conhecimento em Lógica de Predicados

Introdução à Lógica para a Computação

Professor: Adolfo Gustavo Serra Seca Neto

DAINF - UTFPR Curitiba

\end{center}

\newpage

% -----------------------------------------------------------------------------------------
% Apresentação do tema
% -----------------------------------------------------------------------------------------

\begin{spacing}{1.5}

\section{Tema, Descrição do Tema e Integrantes da Equipe}
O presente projeto é baseado no curso de Engenharia da Computação da UTFPR, em suas matérias e professores.

A autoria é do aluno Luca Nozzoli.
\newpage

\end{spacing}

% -----------------------------------------------------------------------------------------
% Frases e fórmulas
% -----------------------------------------------------------------------------------------
 
\section{Frases e Fórmulas}
    
    \subsection{Propriedades de \q{objetos}}
        
        % > veja a ordem dos argumentos! (diferente da tabela pq fica mais lógico escrever assim)
        \frase{Professor(X): X é um professor}{Adolfo Neto é um professor.}{Professor(\q{Adolfo})}
        
        \frase{Aluno(X): X é um aluno}{Luca é um aluno.}{Aluno(\q{Luca})}
        
        \frase{Pessoa(X): X é uma pessoa}{João é uma pessoa}{Pessoa(\q{João})}
        
    \newpage

    \subsection{Relações entre \q{objetos}}
    
        \frase{Leciona(X,Y): X leciona a matéria de Y}{Adolfo leciona a matéria de Lógica}{Leciona(\q{Adolfo},\q{Lógica})}
        
        \frase{Prova(X,Y,Z): X aplica prova dia Y do mês de Z}{ Dorini aplica prova dia 12 do mês de Dezembro}{Prova(\q{Dorini},12,\q{Dezembro})}
        
        \frase{NotaTrabalho(X): retorna a nota que x tirou no trabalho}{A nota de Luca no trabalho foi 10}{NotaTrabalho(\q{Luca})=10}
    
    
    \newpage
        
    \subsection{Negações}
    
        \frase{}{Adolfo não é aluno}{$\neg$ Aluno(\q{Adolfo})}
        
        \frase{Aula(X,Y):retorna duração da aula de X no dia Y da semana }{ A aula de Barreto da terça-feira não tem duração de 2 horas}{$\neg$Aula(\q {Barreto},Terça-feira)=2}
        
        
    \newpage
    
    \subsection{Conjunções}
        
        \frase{}{Luca é aluno e sua nota no trabalho foi 10}{ Aluno(\q{Luca})$\land$ NotaTrabalho(\q{Luca})=10}
        
        \frase{Homem(X): X é homem}{Adolfo é uma pessoa e é homem}{Pessoa(\q{Adolfo})$\land$ Homem(\q{Adolfo})}
        
    \newpage
    
    \subsection{Disjunções}
    
        \frase{Cachorro(X): X é cachorro}{João é uma pessoa ou um cachorro}{ Cachorro(\q{João})$\vee$ Pessoa(\q{João})}
        
        \frase{}{Luca é um professor ou um aluno}{Professor(\q{Luca})$\vee$ Aluno(\q{Luca})}    
        
    \newpage
    
    \subsection{Implicações}
    
        \frase{}{Se Adolfo é professor, então Adolfo não é aluno}{Professor(\q{Adolfo})$\rightarrow$ $\neg$ Aluno(\q{Adolfo})}
        
        \frase{FimSemestre(X): Retorna o dia do fim do semestre}{O fim do semestre 2019/2 é no dia 19}{FimSemestre(2019/2)=19}
        
    \newpage
    
    \subsection{Generalizações Universais}
    
        % quando usar símbolos matemáticos, como \forall, \rightarrow, \exists, etc. colocar entre $ :)
    
        \frase{}{Todo professor leciona uma matéria}{$\forall$x(Professor(X) $\rightarrow$ $\exists$Y Leciona(X,Y))}

        \frase{}{Todo professor aplica prova}{$\forall$x(Professor(X) $\rightarrow$ $\exists$Y$\exists$Z Prova(X,Y,Z))}
        
        \frase{}{Todo aluno tem uma nota no trabalho}{$\forall$x(Aluno(X) $\rightarrow$ $\exists$Y NotaTrabalho(X)=Y)}
        
    \newpage
    
    \subsection{Generalizações Existenciais}
        
        \frase{}{Existe pelo menos uma pessoa que é homem}{$\exists$x(Pessoa(X) $\land$ Homem(X))}
        
        \frase{}{Existe pelo menos um professor cuja aula dure 2 horas}{$\exists$x(Professor(X) $\land$ Aula(X,Y)=2)}
        
        \frase{GostaMatéria(X,Y): X gosta da matéria Y}{Existe pelo menos um aluno que gosta de uma matéria}{$\exists$X $\exists$Y(Aluno(X) $\land$ GostaMatéria(X,Y))}
        
        
    \newpage

% -----------------------------------------------------------------------------------------
% > no nosso caso, não tinha F^3, R^3, etc. Se no seu tiver, é só adicionar ali na lista

% Assinatura
% -----------------------------------------------------------------------------------------

\section{Assinatura}
    
    \vspace{2mm}
    \begin{center} \scalebox{1.2}{$\sum{}{} = [R^1, R^2, R^3, C, F^1, F^2, V]$}\\ \end{center}
    \vspace{2mm}
    
    \conj{$R^1$}{Professor, Aluno, Pessoa, Homem, Cachorro}
    
    \conj{$R^2$}{Leciona, GostaMatéria}
    
    \conj{$C$}{\q{Adolfo}, \q{Luca}, \q{João}, \q{Lógica}, \q{Dorini}, \q{Dezembro}, \q{Barreto}, \q{Terça-feira}, 2, 10, 12, 19, 2019/2}
    
    \conj{$F^1$}{NotaTrabalho, FimSemestre}
    
    \conj{$F^2$}{Aula}
    
    % > se tiver usado alguma outra variável, adicione aqui também
    \conj{$V$}{x,y,z}

\newpage

% -----------------------------------------------------------------------------------------

% Modelos
% -----------------------------------------------------------------------------------------

% > observação: não precisa se importar com a numeração do modelo, nem das constantes (vc1, vc2, ...)
%               usamos latex *magic* pra fazer isso
%               basicamente, alguns contadores que determinam o número do modelo, constante, etc.
%

% > agora vai ser bastante trabalho repetitivo

\section{Modelos}
    
    \novoModelo
    
    \subsection{Exemplo de modelo que satisfaz todas as fórmulas ($\mathcal{M}_\themodelo$)}
        \begin{enumerate}
            
            \item Universo de valores concretos
            
                % vcN até o número que tiver de valores concretos
                \conj{A}{vc1, vc2, vc3, vc4. vc5, vc6, vc7, vc8, vc9, vc10}
            
            \item Constantes
            
                % > como é numerado automaticamente, sugiro escrever % vc(n) depois para saber o que mudar
                %   nas funções e predicados caso troque alguma linha 
                \const{Adolfo} % vc1
                
                \const{Luca} % vc2
                
                \const{Dorini} % vc3
                
                \const{Barreto} % vc4
                
                \const{Terça-feira} % vc5
                
                \const{Dezembro} % vc6
                
                \const{2} % vc7
                
                \const{10} % vc8
                
                \const{12} % vc9
                
                \const{19} % vc10
                
                \const{2019/2} % vc11
                
                \const{1.5} % vc12
                
                \const{Lógica} % vc13
            
            \item Funções

                % Espécie (Soberano Supremo) = Soberano
                \func{NotaTrabalho}{vc2}{vc8} 
                
                 % Espécie (Quatro Braços) = Tetramando
                \func{NotaTrabalho}{...}{vc7}
                
                % Espécie (Vilgax) = Chimera Sui Generis
                \func{FimSemestre}{vc11}{vc10}
                
                \func{FimSemestre}{...}{vc10}
                
                \func{Aula}{vc4,vc5}{vc12}
                
                \func{Aula}{... , ...}{vc7}
                
            \item Predicados
                
                \pred{Professor}{vc1, vc3, vc4}
                
                \pred{Aluno}{vc2}
                
                \pred{Pessoa}{vc1, vc2, vc3, vc4}
                
                \pred{Homem}{vc1, vc2, vc3, vc4}
            
                \pred{Cachorro}{}
                
                \pred{Leciona}{(vc1, vc13)}
                
                \pred{GostaMatéria}{(vc1, vc13), (vc2, vc13)}
                
                \pred{Prova}{(vc3, vc9, vc6)}
                
                
        \end{enumerate}
    \newpage

    \novoModelo % importante!
    
    \subsection{Exemplo de modelo que não satisfaz todas as fórmulas ($\mathcal{M}_\themodelo)$}
        \begin{enumerate}
            
            \item Universo de valores concretos
                
                % vcN até o número que tiver de valores concretos
                \conj{A}{vc1, vc2, vc3, vc4. vc5, vc6, vc7, vc8, vc9, vc10}
                
            \item Constantes
            
                % > como é numerado automaticamente, sugiro escrever % vc(n) depois para saber o que mudar
                %   nas funções e predicados caso troque alguma linha 
                \const{Adolfo} % vc1
                
                \const{Luca} % vc2
                
                \const{Dorini} % vc3
                
                \const{Barreto} % vc4
                
                \const{Terça-feira} % vc5
                
                \const{Dezembro} % vc6
                
                \const{2} % vc7
                
                \const{10} % vc8
                
                \const{12} % vc9
                
                \const{19} % vc10
                
                \const{2019/2} % vc11
                
                \const{1.5} % vc12
                
                \const{Lógica} % vc13
                
            \item Funções

                % Espécie (Soberano Supremo) = Soberano
                \func{NotaTrabalho}{vc2}{vc8} 
                
                 % Espécie (Quatro Braços) = Tetramando
                \func{NotaTrabalho}{...}{vc7}
                
                % Espécie (Vilgax) = Chimera Sui Generis
                \func{FimSemestre}{vc11}{vc10}
                
                \func{FimSemestre}{...}{vc10}
                
                \func{Aula}{vc4,vc5}{vc12}
                
                \func{Aula}{... , ...}{vc7}
                
            \item Predicados
                
                \pred{Professor}{vc1, vc2, vc3, vc4}
                
                \pred{Aluno}{}
                
                \pred{Pessoa}{vc1, vc2, vc3, vc4}
                
                \pred{Homem}{vc1, vc2, vc3, vc4}
            
                \pred{Cachorro}{}
                
                \pred{Leciona}{(vc1, vc13)}
                
                \pred{GostaMatéria}{(vc1, vc13), (vc2, vc13)}
                
                \pred{Prova}{(vc3, vc9, vc6)}
    
        \end{enumerate}

    % > se precisar de mais modelos, insira um \novoModelo e a estrutura da subsection como acima para cada um deles

\end{document}
