# APIs Disponíveis em PHP

Este repositório contém várias APIs úteis para tarefas bancárias e financeiras. As APIs foram desenvolvidas em Python e podem ser utilizadas para facilitar diversas operações, como pagamentos PIX, cobranças bancárias, consultas de conta corrente e poupança.

## APIs Disponíveis

1. **API PIX**

   A API PIX permite que você integre o sistema de pagamento instantâneo brasileiro em suas aplicações. Com esta API, você pode criar e gerenciar pagamentos PIX, consultar transações e muito mais.

2. **API de Cobrança Bancária**

   A API de Cobrança Bancária simplifica o processo de criação e gerenciamento de boletos e cobranças bancárias. Com ela, você pode gerar boletos, verificar o status de cobranças e automatizar tarefas de cobrança.

3. **API de Conta Corrente**

   A API de Conta Corrente permite acessar informações sobre contas correntes em instituições financeiras. Você pode consultar o saldo, extrato, histórico de transações e muito mais.

4. **API Poupança**

   Com a API de Poupança, você pode acessar informações sobre contas poupança, incluindo saldos, rendimentos, depósitos e retiradas.

## Como Usar

Cada API possui sua própria documentação e exemplos de uso. Certifique-se de consultar a documentação específica de cada API para obter informações detalhadas sobre como começar a utilizá-las.

## Exemplos

Nesta seção, serão fornecidos alguns exemplos básicos de como usar cada API:

### Exemplo de Uso da API PIX

```php
<?php
  $data = [
      'grant_type' => 'client_credentials',
      'client_id' => '{client_id}',
      'scope' => 'cob.read cob.write cobv.write cobv.read lotecobv.write lotecobv.read pix.write pix.read webhook.read webhook.write payloadlocation.write payloadlocation.read',
  ];

  $certPath = 'caminho_onde_ta_certificado';
  $certPassword = 'senhadocertificado';
  $tokenUrl = 'https://auth.sicoob.com.br/auth/realms/cooperado/protocol/openid-connect/token';
  $curl = curl_init();

  // Configura as opções do CURL
  curl_setopt($curl, CURLOPT_URL, $tokenUrl);
  curl_setopt($curl, CURLOPT_POST, true);
  curl_setopt($curl, CURLOPT_POSTFIELDS, http_build_query($data));
  curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

  // Configura o certificado PFX
  curl_setopt($curl, CURLOPT_SSLCERT, $certPath);
  curl_setopt($curl, CURLOPT_SSLCERTPASSWD, $certPassword);
  curl_setopt($curl, CURLOPT_SSLCERTTYPE, 'P12');

  // Executa a solicitação CURL
  $response = curl_exec($curl);

  // Verifica se houve algum erro
  if (curl_errno($curl)) {
      echo 'Erro ao fazer a requisição: ' . curl_error($curl);
  } else {
      $tokenData = json_decode($response, true);
      if (isset($tokenData['access_token'])) {
          $accessToken = $tokenData['access_token'];
          echo 'Token de acesso:<br><br>' . $accessToken;
      } else {
          echo 'Erro ao obter o token:<br><br>' . $response;
      }
  }

  curl_close($curl);
```

Lembre-se de substituir `'client_id'`, `'caminho_onde_ta_certificado'`, `'senhadocertificado'` e outras informações relevantes pelos valores apropriados em seus casos de uso.

## Contribuição

Se você deseja contribuir para este projeto ou relatar problemas, sinta-se à vontade para abrir um problema ou enviar uma solicitação pull. Sua contribuição é bem-vinda!

---

Esperamos que estas APIs em Python sejam úteis para suas necessidades bancárias e financeiras. Se você tiver alguma dúvida ou precisar de suporte adicional, não hesite em entrar em contato conosco.
Atravês do WhatsApp. Basta escrever o termo **#API** e enviar para o número **61 4000-1111**. O time de suporte estará disponível para atendê-lo das **09h** às **18:30** durante os dias úteis.
