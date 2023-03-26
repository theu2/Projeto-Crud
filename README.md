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
Faça o download do programa de Banco de Dados MySql, com a função de criar e armazenar as funções (cadastro,atualizações e delete de informações) no site <https://www.mysql.com/downloads/><br>
![MySql](mysql.png)

* **Passo 4:**
Criar o Banco de Dados no programa do MySql<br>
![Banco](banco.png)
                
* **Passo 5:**
Montar a estrura no arquivo index ou seja o corpo do seu projeto<br>
                
             
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

* **Passo 6:**
Criar uma pasta Controllers onde ficará armazenado todos os arquivos de manipulação do Banco de Dados e suas funções:
  
  1.Função de atualização de dados:
      
      <?php
          include("../models/conexao.php");
             mysqli_query($conexao, "UPDATE alunos SET nome='".$_POST["alunoNome"]."', cidade='".$_POST["alunoCidade"]."', sexo='".$_POST["alunoSexo"]."' WHERE codigo = ".$_POST["alunoCodigo"]);
              header("location:../");
      ?>
  
  2.Função de cadastro:
  
      <?php
        include("../models/conexao.php");
          mysqli_query($conexao, "UPDATE alunos SET nome='".$_POST["alunoNome"]."', cidade='".$_POST["alunoCidade"]."', sexo='".$_POST["alunoSexo"]."' WHERE codigo = ".$_POST["alunoCodigo"]);
            header("location:../");
      ?>

  3.Função de deletar dados:
  
      <?php
        include("../models/conexao.php");
          mysqli_query($conexao,"DELETE FROM alunos WHERE codigo = ".$_GET["ida"]);
            header("location:../");
      ?>
      
  4.Função:
  
      <?php
        include("../models/conexao.php");
          mysqli_query($conexao,"DELETE FROM alunos WHERE codigo = ".$_GET["ida"]);
            header("location:../");
      ?>
      
 * **Passo 7:**
 Criar uma pasta models onde ficará armazenado o arquivo de conexão com o Banco de Dados:
 
             <?php
               $conexao = mysqli_connect("127.0.0.1","root","");
                mysqli_select_db($conexao,"escola");
                  mysqli_set_charset($conexao,"UTF8");
             ?>
             
* **Passo 8**:
Criar uma pasta views que ficará armazenado as telas de Cadastro e Atualizar Cadastro:
          
  1.Cadastro:
  
            <?php include("blades/header.php") ?>
              <div class="container border rounded mt-5 bg-white shadow">
                <form action="../controllers/cadastrarAluno.php" method="post">
                  <div class="row">
                    <div class="col">
                      <label class="form-label">Nome</label>
                        <input class="form-control" type="text" name="alunoNome"><br>
              </div>
              <div class="col">
                <label class="form-label">Cidade</label>
                  <input class="form-control" type="text" name="alunoCidade"><br>
              </div>
              </div>
              <input class="form-check-input"type="radio" value="m" name="alunoSexo">
                <label class="radio-inline"> Masculino </label><br>
                  <input class="form-check-input" type="radio" value="f" name="alunoSexo">
                    <label class="radio-inline"> Feminino </label><br>
                      <input class="mt-2 mb-3 btn btn-success" type="submit" value="Cadastrar">
              </form>
              </div>
                <?php include("blades/footer.php") ?>
                
  2.Atualizar:
            
            <?php include("../models/conexao.php") ?>
              <?php include("blades/header.php") ?>
            <?php
              $varIda = $_GET["ida"];
                $query = mysqli_query($conexao,"SELECT * FROM alunos WHERE codigo = $varIda");
                  while($exibe = mysqli_fetch_array($query)){
            ?>
            <div class="container border rounded mt-5 bg-white shadow">
              <form action="../controllers/atualizarAluno.php" method="post">
                <input type="hidden" name="alunoCodigo" value="<?php echo $exibe[0] ?>">
                  <div class="row my-3">
                    <div class="col">
                      <label class="form-label">Nome</label>
                        <input class="form-control" type="text" name="alunoNome" value="<?php echo $exibe[1] ?>"><br>
            </div>
            <div class="col">
              <label class="form-label">Cidade</label>
                <input class="form-control" type="text" name="alunoCidade" value="<?php echo $exibe[2] ?>"><br>
            </div>
            </div>
              Masculino <input type="radio" value="m" name="alunoSexo" <?php echo ($exibe[3]=="m")?"checked":""?>><br>
              Feminino  <input type="radio" value="f" name="alunoSexo" <?php echo ($exibe[3]=="f")?"checked":""?>><br>
                <input class="mt-2 mb-3 btn btn-success" type="submit" value="Atualizar">
            </form>
            </div>
            <?php } ?>
            <?php include("blades/footer.php") ?>
            
            
