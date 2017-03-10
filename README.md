XLS-DIFF
--
This repository demonstrates how to configure git such that excel files can be kept in version control with textual diffs.


INSTALLATION
--
Install xls2txt:

    git clone https://github.com/hroptatyr/xls2txt
    cd xls2txt/
    make
    make install -s xls2txt /usr/local/bin


Install xlsx2txt:

    brew install go
    git clone https://github.com/shibukawa/xlsx2txt
    cd xlsx2txt/
    make get
    make build
    cp xlsx2txt /usr/local/bin/
    

Configure local git repository:

- edit .gitattributes

		*.xls diff=xls
		*.xlsx diff=xlsx

- edit .git/config

    	[diff "xls"]
        	binary = true
        	textconv = /usr/local/bin/xls2txt

	    [diff "xlsx"]
   	     	binary = true
        	textconv = /usr/local/bin/xlsx2txt

Henceforth git diff should yield readable text outputs on .xls/.xlsx files under version control, rather than only stating that the binary files differ.  For a demonstration, Try modifying the test.xlsx file locally and typing `git diff`.

--
QED | http://qed.ai
