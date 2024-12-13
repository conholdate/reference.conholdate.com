---
title: Converta DOCX para MHTML e envie e-mail usando Aspose.Words para .NET
linktitle: Converta DOCX para MHTML e envie e-mail usando Aspose.Words para .NET
second_title: API de processamento de documentos Aspose.Words
description: Este guia abrangente fornece um tutorial passo a passo sobre como converter documentos DOCX para o formato MHTML e enviá-los por e-mail usando as bibliotecas Aspose.Words e Aspose.Email no .NET.
type: docs
weight: 10
url: /pt/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Introdução

No cenário digital de hoje, converter documentos entre formatos e enviá-los por e-mail é uma tarefa comum. Este guia o guiará pela conversão de um arquivo DOCX para o formato MHTML e pelo envio por e-mail usando as poderosas bibliotecas Aspose.Words e Aspose.Email para .NET. Vamos detalhar cada etapa claramente, garantindo que você possa acompanhar com facilidade. Vamos começar!

## Pré-requisitos

Antes de mergulhar no processo, certifique-se de ter a seguinte configuração:

1.  Aspose.Words para .NET: Baixe e instale a biblioteca do[Página de lançamentos da Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email para .NET: Baixe e instale esta biblioteca do[Página de lançamentos da Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.
4. Servidor SMTP: você precisará de acesso a um servidor SMTP para enviar e-mails.

## Importando namespaces necessários

Para utilizar Aspose.Words e Aspose.Email em seu projeto, você deve importar os namespaces necessários. Adicione as seguintes diretivas using no topo do seu arquivo C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Etapa 1: Carregue o documento DOCX

 Comece carregando o documento DOCX que você deseja converter. Use o`Document` classe do Aspose.Words para fazer isso.

```csharp
// Especifique o caminho para o diretório do seu documento.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Etapa 2: Salve o documento como MHTML

 Em seguida, converta o documento carregado para o formato MHTML. Isso é feito usando o`Save` método do`Document`aula.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Redefina a posição do fluxo para o início da leitura.
    stream.Position = 0;
}
```

## Etapa 3: Crie uma mensagem de e-mail

Agora, crie uma mensagem de e-mail do fluxo MHTML usando Aspose.Email. Você utilizará o`MailMessage` classe para esse propósito.

```csharp
// Carregue o fluxo MHTML em uma mensagem de e-mail MIME Aspose.Email.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Etapa 4: Envie o e-mail

 Por fim, envie o e-mail usando um cliente SMTP. Configure o cliente SMTP com os detalhes do seu servidor e use o`Send` método para despachar a mensagem.

```csharp
// Configure e envie a mensagem usando Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Conclusão

Parabéns! Você converteu com sucesso um documento DOCX para MHTML e o enviou por e-mail usando Aspose.Words e Aspose.Email para .NET. Este processo envolve carregar o documento, convertê-lo para MHTML, criar uma mensagem de e-mail e enviá-la por meio de um cliente SMTP. Com estas etapas, você pode automatizar a conversão e o envio de documentos por e-mail perfeitamente em seus aplicativos.

## Perguntas frequentes

### Posso usar esse método para converter outros formatos de documento?
Absolutamente! O Aspose.Words suporta uma ampla variedade de formatos, permitindo que você converta DOC, DOCX, RTF e mais para MHTML.

### Como posso adicionar anexos ao e-mail?
 Você pode adicionar anexos facilmente usando o`Attachments` propriedade do`MailMessage`aula.

### O Aspose.Words é compatível com o .NET Core?
Sim, o Aspose.Words é compatível com o .NET Core, o que o torna adequado para uso em aplicativos .NET Core.

### Preciso de uma licença para Aspose.Words e Aspose.Email?
 Sim, ambas as bibliotecas exigem uma licença. Você pode obter uma licença temporária para fins de avaliação no[Aspose página de compra](https://purchase.conholdate.com/temporary-license/).

### Onde posso encontrar mais documentação?
 Para documentação detalhada, confira Aspose.Words[aqui](https://reference.aspose.com/words/net/) e Aspose.Email[aqui](https://reference.aspose.com/email/net/).