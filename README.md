# Envio_de_email_com_python
# Arquivo 1 Python - codigo

import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from time import sleep
from credenciais import email, password


def enviar_email(destinatario, assunto, corpo):
    # Configurações do servidor SMTP do Outlook
    servidor_smtp = "smtp.office365.com"
    porta_smtp = 587
    usuario = (email)
    senha = (password)

    # Configuração do e-mail
    mensagem = MIMEMultipart()
    mensagem["From"] = usuario
    mensagem["To"] = destinatario
    mensagem["Subject"] = assunto
    mensagem.attach(MIMEText(corpo, "plain"))

    # Conecta-se ao servidor SMTP e envia o e-mail
    with smtplib.SMTP(servidor_smtp, porta_smtp) as servidor:
        servidor.starttls()  # Habilita a criptografia TLS
        servidor.login(usuario, senha)
        servidor.send_message(mensagem)


# Exemplo de uso
destinatario = "Digite o email no qual voce quer enviar a menssagem"
assunto = "Assunto do e-mail"
corpo = "Corpo do e-mail"

# Tempo de envio de e-mail
print("Enviando e-mail...")
sleep(10)
print("E-mail enviado!")

enviar_email(destinatario, assunto, corpo)

# Arquivo 2 python - credenciais do email
nome = "Digite seu email"
password = "digite a senha do seu email"
