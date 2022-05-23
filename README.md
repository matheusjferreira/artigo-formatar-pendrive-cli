> # Formatar Pen Drive CLI

> ### O Artigo:

Em determinado momento, tive a dificuldade de formatar um de meus pen drives no windows, isso porque havia feito dele um pen drive bootável com uma imagem de um OS. Programas como Rufus não funcionaram, então achei com dificuldade a solução, e por isso esse passo a passo existe.
Neste caso vamos usar o cmd (pronpt de comando) no Windows e o terminal no Linux, para executar alguns "comand lines" (cli).

![sudo](https://user-images.githubusercontent.com/59848966/115727608-2353a300-a35a-11eb-8570-8a15577e452c.jpg)

> ## Windows:

Para formatar o pen drive usaremos o "diskpart":


Execute no cmd:

	diskpart

> :warning: Irá pedir permissão do administrador, conceda.

Liste os discos conectados:

	list disk

Selecione o pen drive (no meu caso é o disco "1"):

	select disk 1

Formate com o comando:

	clean

Crie uma nova partição:

	creat partition primary
	

A saída deve ser assim:

![formate_windows1](https://user-images.githubusercontent.com/59848966/115734319-fd310180-a35f-11eb-9ccc-8a8986ab0134.png)


Pronto, seu pen drive está pronto para uso novamente!


> ## Linux:

Abra o terminal linux, e use o comando a seguir para listar os discos:

	$ sudo fdisk -l

Desmonte a partição do seu pen drive (no meu caso o pen drive é o disco "sdc", logo a partição primária dele a qual quero formatar é "sdc1"):

	$ sudo umount /dev/sdac1

Por fim, formate com o comando:

	$ sudo mkntfs -Q -v -F -L 'black' '/dev/sdc1'
	
Explicação dos parâmetros:

	-Q => Execute uma formatação rápida
	-v => Execução verbosa/detalhada.
	-F => Força a execução apesar dos erros.
	-L => Defina o rótulo do volume.

A saída deve ser assim:


![format_linux1](https://user-images.githubusercontent.com/59848966/115734322-fdc99800-a35f-11eb-97bd-ff4b5d8bd0a6.png)


![format_linux2](https://user-images.githubusercontent.com/59848966/115734329-fe622e80-a35f-11eb-9b4a-e60d89316d2a.png)


![format_linux3](https://user-images.githubusercontent.com/59848966/115734331-fe622e80-a35f-11eb-8082-7ad3a0bf4f26.png)


Pronto, seu pen drive está pronto para uso novamente!

> ## Licença

	MIT License

	Copyright (c) 2022 Matheus Ferreira

	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:

	The above copyright notice and this permission notice shall be included in all
	copies or substantial portions of the Software.

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
	SOFTWARE.
