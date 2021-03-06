:octocat:
- Why do we use the terminal in bioinformatics?
    - It allows reproducibility of our actions, because we do our work as scripts. Any other person can simply execute the same script on their
    terminal to gt the same results (including our mistakes, but at least it's the same)
    
- What is a plain text file?
    - Plain text, as oppposed to rich text, is simply a stream of characters of a given encoding (like UTF-8). This way, it can be read and displayed by virtually
    anyone with very basic tools. Any special features, like for example headers for markdown or HTML, are not saved in some obscure metadata, but are rather part
    of that same stream of characters, and only because the program that displays them knows the syntax can they be translated into things other than simple characters.
    
- In bioinformatics, most of the data are stored in plain text files with added syntax/structure (and commonly compressed afterwards). For instance,
fasta or fastq files we have discussed them today, but also SAM, BED, GTF, VCF and others (to be discussed next week). Why is that?
    - Because plain text is a very accessible way of storing data, and because we want to work with command line tools, which are not equipped to interact with
    rich text intimately.

- How can we list files are in a directory? Please provide the command(s).
    - `ls` to list contents of the current directory, if needed with the `-l` tag.

- What | and > do in a terminal?
    - `|`allows chaining commands to gether. the result of the earlier command is used as the input of the later command.
    - `>`takes the output of the stuff on the left and puts it into a file names as what you put on the right.

- How do we print the last 10 lines of the file named /mnt/test/test.txt? Please provide the command(s).
    - `tail /mnt/test/test.txt`

- How do we print the first column of the file named /mnt/test/test.txt whose columns are separatedby tabs? Please provide the command(s).
    - `awk '{print $1}' /mnt/test/test.txt`

- How can we print every third line of a text file? Please provide the command(s), and discuss what they do.
    - ``awk 'NR%3==0' file_name.txt`` basically goes on each line, then divides the current line number (NR), divides it by 3 and takes the remainder of that division.
    If the remainder equals 0, that line is printed.

- How can we transform FASTQ into FASTA files using standard Unix tools (sed, awk, etc)? Please provide the command(s), and discuss what they do.
    - ``awk 'NR % 4 == 1 {print ">"$1}; NR % 4 == 2 {print}' SP1.fq`` takes the first line of each group of 4 (the sequence identifier), adds a `>` before
    it and keeps that, then also keeps the second line (the genomic code) and keeps that as is, and ignores the other lines. The lines are identified using
    modulo as explained before.
