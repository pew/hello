# vim
## vim gpg
### ~/.vimrc
    set noswapfile

### edit existing file
    gpg -d file.gpg|vim -

### write file
    :%!gpg -a -e
    :%!gpg -a -e -r user@mail.com

### create new file
    vim bla.gpg
    :%!gpg -a -e
    :x
    
## tips & tricks 
### close all windows
    :qa!

### all lowercase
without visual

	ggguG
	
with visual

	ggVGu
