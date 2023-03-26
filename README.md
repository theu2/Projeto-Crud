# Projeto-Crud
Projeto de Cadastro e Consulta simples 

CRUD (Creat, Read, Update, Delete) é um acrônimo para as maneiras de se operar em informações armazenada. Crud tipicamente refere-se a operações perfomadas em um banco de dados ou base de dados, mas também pode aplicar-se para funções de alto nível de uma aplicação, como exclusões reversíveis, onde a informação não é realmente deletada, mas é maracada como deletada via status.

Passo a passo para criar um sistema de cadastro e consulta simples utilizando o Crud.

* **Passo 1:**
Faça o download do programa de servidor chamado Xampp, é possivel realizar no site <https://www.apachefriends.org/pt_br/download.html><br>
Selecione as configurações desejadas.<br>
![XAMPP](xamp1.jpg)

* **Passo 2:**
Faça o download do programa Visual Code para alteração e manipulação dos Códigos de sua vontade no site <https://code.visualstudio.com/Download><br>
Selecione as configurações desejadas <br>
![Visual Code](visual1.png)

* **Passo 3:**
Montar a estrura no arquivo index ou seja o corpo do seu projeto<br>
                
                ```php
                <?php 
                    include("views/blades/header.php"); 
                        include("controllers/funcoes.php");
                ?>
                <div class="container bg-white rounded-2 mt-5 pt-3 pb-3 ps-3 pe-3 shadow">
                    <a href="views/cadastro.php"><buttom type="buttom" class="btn btn-success">Cadastrar</buttom></a>
                <hr>
                <form action="index.php" method="post">
                    <input class="form-control" type="text" name="buscar" size="30" placeholder="Buscar">
                </form>
                <hr>
                <?php 
                    mostrarDados(); ?>
                </div>
                <?php
                  include("views/blades/footer.php")
                 ?>
                ```
