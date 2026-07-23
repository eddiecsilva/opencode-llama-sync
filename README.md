# OpenCode LLama Sync

Script para automação do cadastro de novos modelos do **llama-cpp** no **opencode.json**.

## Descrição

Este script simplifica o processo de registro de modelos do **llama-cpp** no arquivo **opencode.json**, utilizando um provedor personalizado. É especialmente útil durante a fase de pesquisa e validação de modelos para usos específicos, reduzindo erros manuais na edição do arquivo.

### Recursos

- Realiza uma cópia de segurança do arquivo original **opencode.json**;

- **Detecta e configura automaticamente o tamanho do contexto** do modelo LLama (ex: `context_size`), que influencia diretamente o limite de tokens que o modelo pode processar.
  - **Utilidade**: Garante que o OpenCode utilize a capacidade máxima de contexto do modelo LLama, evitando truncamentos ou erros na geração de respostas.
  - Exemplo: Um modelo com `context_size: 4096` permitirá interações mais longas e detalhadas.
- Lista todos os modelos disponíveis no **llama-cpp**;
- Cria um **provider** no **opencode.json** com todos os modelos cadastrados.

## Tecnologias Utilizadas

- **llama-cpp**: Biblioteca para executar modelos LLama de forma local.
- **OpenCode**: Plataforma de automação de código que utiliza o arquivo **opencode.json** para configurar provedores de modelos.

# Variáveis opcionais:
- LLAMA_BASE_URL=http://127.0.0.1:8085/v1
- OPENCODE_PROVIDER_ID=llamacpp-local
- OPENCODE_PROVIDER_NAME="llama.cpp local"
- OPENCODE_CONTEXT=32768 #pode variar de acordo com sua configuração local
- OPENCODE_OUTPUT=4096 #pode variar de acordo com sua configuração local
- OPENCODE_DEFAULT_MODEL=<id retornado por /v1/models>
- OPENCODE_CONFIG_FILE=$HOME/.config/opencode/opencode.json

## Instalação

### Pré-requisitos
- **Python 3.9+** (para execução do script).
- **llama-cpp** em execução local com modelos já baixados.

### Passo a Passo

1. **Clone este repositório**:
   ```bash
   git clone https://github.com/eddiecsilva/opencode-llama-sync
   ```

2. **Copie o script para um diretório executável** (recomendado `~/.local/bin`):
   ```bash
   cp opencode-llama-sync ~/.local/bin/opencode-llama-sync
   ```

3. **Conceda permissão de execução**:
   ```bash
   chmod +x ~/.local/bin/opencode-llama-sync
   ```

4. **Garanta que o `opencode.json` esteja acessível** no diretório raiz do OpenCode.

## Uso

### Execução Básica

- Edite o arquivo "opencode-llama-sync" e ajuste a variável LLAMA_BASE_UR de acordo com o seu ambiente.
- Execute o script a partir do terminal para registrar automaticamente os modelos do **llama-cpp** no **opencode.json**.

```bash
opencode-llama-sync
```

### Parâmetros

- **Cria uma cópia de segurança** do arquivo original (`opencode.json.bak`).
- **Exige que o `llama-cpp` esteja em execução** na porta padrão (`8080` por padrão).

### Dicas

- Certifique-se de que o **llama-cpp** esteja rodando com os modelos desejados antes de executar o script.
- O script **sobrescreve a seção de provedores** no `opencode.json` automaticamente.

## Contribuição

Contribuições são bem-vindas! Siga os passos abaixo para contribuir:

1. **Fork** este repositório.
2. Crie uma **nova branch** para sua feature ou correção.
3. Faça suas alterações e **commit** com mensagens claras.
4. Envie um **pull request** para revisão.

## Aviso de Uso

⚠️ **Aviso Importante**

Este script foi desenvolvido **exclusivamente para uso pessoal em meu laboratório** e é distribuído **sem garantias ou suporte**. Utilize por sua própria conta e risco.
