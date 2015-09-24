
<?php

echo "<html>
<head>
<title> Processando... </title>
<link rel=\"stylesheet\" href=\"class.css\" type=\"text/css\">
</head>";

$nome = $_POST['nome'];
$email = $_POST['email'];
$assunto = $_POST['assunto'];
$mensagem = $_POST['mensagem'];

$ip = $_SERVER['REMOTE_ADDR'];

$mail_destino = "contato@wefmecanica.com.br";
echo "<body bgcolor=\"#FFFFFF\" leftmargin=\"10\" topmargin=\"10\" marginwidth=\"0\" marginheight=\"0\">
<center><font class=\"texto\">";

$mail_header = "Mensagem do SITE.";

$msg_reply = "Olá $nome,\nRecebemos o seu email com o assunto $assunto.\n\nObrigado pelo seu contato!\n\n Esta é uma mensagem automática de confirmação.\n Por Favor não responda este e-mail.\n $ip";

$msg_erro = "Atenção!! Os campos (Nome, E-mail e Mensagem ) não podem estar em branco.";


if ($nome!="" and $assunto!="" and $email!="")
  {
  $msg.="$mail_header\n\n";
  $msg.="Nome: $nome\n";
  $msg.="Cidade: $cidade\n";
  $msg.="Estado: $estado\n";
  $msg.="Email: $email\n";
  $msg.="Assunto: $assunto\n";
  $msg.="Mensagem: $mensagem\n";
  $msg.="ip da origem: $ip";

  if (mail($mail_destino, "Formulário do SITE: $assunto", $msg, "From:$nome<$email>"))
    {

    echo 
      " </font></center>
      <html>
      <meta http-equiv=refresh content=10;URL=./></html>";
      echo "<font class=\"texto\">";
      echo "<b>olá! $nome</b>,<br><br>sua mensagem:<br> <font color=\"#FF0000\"><b>$mensagem </b></font><br>Foi enviada com sucesso!<br><br>";
      echo "Obrigado!<br>você receberá um e-mail de confirmação desta mensagem<br><br>endereço ip: <b>$ip</b></font> 
      ";
   
     mail("$nome<$email>", "Re:Formulário enviado: $assunto", $msg_reply, "From:<$mail_destino>");
    }
    else
    echo
      "
      <meta http-equiv=refresh content=3;URL=../>
      </html><center><br><br><font color=red>
      <b>Erro ao enviar e-mail!</b>
      </font></center>
      ";
  }
else
  {

  echo 
    "
    <br><br><center>
    $msg_erro <br><br>
    <a href=\"javascript:window.history.go(-1)\" class=\"links\">Por favor, volte e preencha corretamente.</a>
    </center>
    ";
  }

?>
