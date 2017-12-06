Phrack.org issues as PDF philes

If you want to generate it yourself:

`$ mkdir phrack`

`$ cd phrack`

## Download
`$ for i in $(seq 1 69); do wget -c http://phrack.org/archives/tgz/phrack$i.tar.gz; done`

69 is the latest issue as of this writing

## Extract
`$ for i in $(ls -1 *.tar.gz); do newdir=${i:r:r}; mkdir $newdir; tar zxvf $i -C $newdir; done`

`${i:r:r}` is to remove file extension in zsh. If you use bash or something else, edit accordingly.

## Create PDF
`$ sudo apt install enscript`

`$ for i in ``ls -1v | grep phrack``; do cd $i; enscript -p $i.ps ``ls -v *.txt``; ps2pdf $i.ps $i.pdf; rm -rf $i.ps; cd ..; done`

`$ mkdir pdfs`

`$ cp phrack*/*.pdf pdfs` # again, I think this only works with zsh. Edit accordingly for your shell of preference.
