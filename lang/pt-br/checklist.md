## Conceitos
- [ ] Verifique se seu app segue a [filosofia Unix](https://en.wikipedia.org/wiki/Unix_philosophy): "Faça uma coisa, e faça bem"
- [ ] Verifique se a descrição do seu app encaixa em poucas palavras
  * Exemplos:
  [django-taggit](https://github.com/alex/django-taggit): django-taggit a simpler approach to tagging with Django.  
  [django-js-reverse](https://github.com/ierror/django-js-reverse): Javascript URL handling for Django that doesn't hurt.  
  [django-impersonate](https://bitbucket.org/petersanchez/django-impersonate): Simple application to allow superusers to "impersonate" other non-superuser accounts.  

- [ ] Verifique se a descrição do seu app tem a palavra "e", e caso tenha, tente quebrar em mais aplicações

## Fácil para Instalar
- [ ] Crie um arquivo [LICENSE](https://choosealicense.com/)

- [ ] [Distribua no PyPI](https://packaging.python.org/distributing/)
  * - [ ] Nome com prefixo django-
  * - [ ] Cheque conflito de nomes
    * Este é um mau exemplo de [django-filter](https://pypi.python.org/pypi/django-filter) vs [django-filters](https://pypi.python.org/pypi/django-filters)
  * - [ ] Use [Wheels](https://packaging.python.org/distributing/#wheels)

- [ ] Publique em [Django Packages](https://djangopackages.org/)

- [ ] Instale dependências automaticamente
  * - [ ] Adicione dependências em `install_requires` no setup.py
  * - [ ] Não adicione Django em `install_requires`
  * - [ ] Não coloque versões com `==` em `install_requires`. Use `>=`

- [ ] Verifique se você precisa de uma aplicação Django ou um pacote Python regular
  * Aplicações Django precisam ser adicionados em `INSTALLED_APPS`. Pacotes python não. Exemplos de pacotes Python:
  [django-templated-email](https://github.com/vintasoftware/django-templated-email)
  [django-hashid-field](https://github.com/nshafer/django-hashid-field)
  [django-downloadview](https://github.com/benoitbryon/django-downloadview)

- [ ] Tenha padrões sensatos e inteligentes
  * - [ ] Torne-o um padrão
  * - [ ] Não obrigue copiar e colar de trechos de código
  * - [ ] Não faça nada perigoso por padrão, como caching

- [ ] Exija que o comportamento inseguro seja explícito
  * Não exiba tudo se algo não estiver definido, exemplo: `fields = None` não deve significar todos os campos

- [ ] Tenha propriedades declarativas para habilitar uma fácil configuração
  * - [ ] Adicione um prefixo para todas as propriedades da aplicação, como `MYAPP_SETTING_KEY`
  * - [ ] Converta parâmetros internos hardcoded para propriedades
    * Por exemplo, `AVATAR_MAX_SIZE` do [django-avatar](http://django-avatar.readthedocs.io/en/latest/#AVATAR_MAX_SIZE) deve ser hardcoded, mas ele é uma configuração
  * - [ ] Se é necessário frequentemente por desenvolvedores, habilite o comportamento para ser alterado com somente uma alteração na configuração
  * - [ ] Se é necessário frequentemente por desenvolvedores, aceite classes customizadas e funções nas configurações via dotted path
    * Por exemplo, [django-taggit](https://django-taggit.readthedocs.io/en/latest/custom_tagging.html#using-a-custom-tag-string-parser) suporta tag parsers customizados via configuração

- [ ] Suporte pipelines declarativos para workflows configuráveis
  * Cheque a implementação de [python-social-auth](http://python-social-auth-docs.readthedocs.io/en/latest/configuration/django.html#personalized-configuration)

- [ ] Providencie views padronizados com templates e URLs para habilitar a aplicação para ser incluída facilmente

- [ ] Tenha uma política de upgrade amigável
  * - [ ] Torne deprecated antes de remover. Para raise deprecation warnings, use o módulo [warnings](https://docs.python.org/3/library/warnings.html) do Python
  * - [ ] Não reescreva migrações
    * Os usuários podem depender dos seus antigos arquivos de migração, porque eles rodaram no passado
  * - [ ] [Mantenha um CHANGELOG](http://keepachangelog.com/)
  * - [ ] Siga o [Versionamento Semântico](http://semver.org/)

- [ ] Dê créditos, tenha um arquivo [AUTHORS](https://github.com/django/django/blob/master/AUTHORS)
  * Verifique este [script](https://kev.inburke.com/kevin/easy-maintenance-of-your-authors-file/) para gerar um arquivo AUTHORS a partir do histórico do seu repositório GIT

## Fácil de Usar
- [ ] Providencie uma documentação
  * - [ ] Escreva docs primeiro
  * - [ ] Tenha um README
  * - [ ] Providencie um tutorial quick start descrevendo os casos mais comuns
  * - [ ] Separe documentação de alto e baixo nível
  * - [ ] Use pronomes de gênero neutros
  * - [ ] Hospede isso em [Read the Docs](http://readthedocs.org/)

- [ ] Escreva testes
  * - [ ] Teste com um [custom user model](https://docs.djangoproject.com/en/dev/topics/auth/customizing/#specifying-a-custom-user-model)
  * - [ ] Providencie uma [cobertura de código](http://coverage.readthedocs.io/en/latest/)

- [ ] Tenha uma Integração Contínua
  * - [ ] Use [tox](https://tox.readthedocs.io/en/latest/) para testar com as mais variadas versões de Python e django
    * Cheque o tox.ini de projetos populares como [django-filter](https://github.com/carltongibson/django-filter/blob/develop/tox.ini) e [django-taggit](https://github.com/alex/django-taggit/blob/master/tox.ini)
  * - [ ] Respeite o PEP 8, use [flake8](https://gitlab.com/pycqa/flake8)

- [ ] Envie com um projeto de exemplo
  * Exemplos de implementações:  
  [django-guardian](https://github.com/django-guardian/django-guardian/tree/devel/example_project)
  [django-haystack](https://github.com/django-haystack/django-haystack/tree/master/example_project)
  [django-avatar](https://github.com/grantmcconnaughey/django-avatar/tree/master/test_proj)

- [ ] Separe abstrações Django em nomes de [arquivos comumente usados](https://gist.github.com/fjsj/65ecfec09cfd2a684d53294d01677b9b) como views.py, forms.py, fields.py, etc.

- [ ] Siga o padrão `resource_action` em nomes de URLs, como `password_reset` ou `product_detail`

- [ ] Nunca confie em modelos de usuário padrão, suporte [custom user models](https://docs.djangoproject.com/en/dev/topics/auth/customizing/#specifying-a-custom-user-model)
  * Cheque a implementação de [django-registration](http://django-registration.readthedocs.io/en/latest/custom-user.html)

- [ ] Providencie uso declarativo
  * Exemplo de implementações:
  [django-filter filtersets](https://django-filter.readthedocs.io/en/develop/guide/usage.html#generating-filters-with-meta-fields)
  [django-import-export resources](http://django-import-export.readthedocs.io/en/latest/getting_started.html#advanced-data-manipulation)

- [ ] Não conecte código implicitamente pelo nome ou módulo. Tenha um registry
  * Exemplos de implementações:
  [django-contrib-comments moderator registry](http://django-contrib-comments.readthedocs.io/en/latest/moderation.html#module-django_comments.moderation)
  [django-activity-stream registry](http://django-activity-stream.readthedocs.io/en/latest/configuration.html)

- [ ] Tenha comandos management para necessidades em comum de desenvolvedores
  * Exemplo de implementações:
  [django-reversion commands](http://django-reversion.readthedocs.io/en/latest/commands.html)
  [django-haystack commands](http://django-haystack.readthedocs.io/en/latest/tutorial.html)

- [ ] Use `_default_manager`, não `objects`, quando interagir com models do projeto host

- [ ] Seja pythônico
  * - [ ] Use generators para lazy evaluation
  * - [ ] Use declarações de contexto `with` para lidar com recursos não gerenciados

- [ ] Previna erros
  * - [ ] Providencie checks com [Django System check framework](https://docs.djangoproject.com/en/dev/topics/checks/)

- [ ] Falha rápida
  * - [ ] Dispare `ImproperlyConfigured` se o desenvolvedor cometer erros na configuração
    * Por exemplo, [django-filter dispara `ImproperlyConfigured`](https://github.com/carltongibson/django-filter/blob/0883cb6b25cd3bb2fa337fb9c54f0a3d2159f676/django_filters/views.py#L18-L28) quando o desenvolvedor esquece de especificar `filterset_class` ou `model` no `FilterView`
  * - [ ] Dispare `TypeError` ou `ValueError` quando a aplicação obtém um argumento inválido

- [ ] [Internacionalize](https://docs.djangoproject.com/en/dev/topics/i18n/translation/) (I18N) seus strings

## Fácil para integrar
- [ ] Reduza descontinuidades na integração
  * - [ ] Quebrar comportamentos de classes dentro de métodos
  * - [ ] Separar comportamento de classes dentro de mixins
  * - [ ] Isolar lógica dentro de módulos helper com funções e classes de negócio

- [ ] [Use `AppConfig`](https://docs.djangoproject.com/en/dev/ref/applications/)
  * - [ ] Verifique se seu aplicativo não interrompe quando o AppConfig é estendido

- [ ] Providencie templates padrão
  * - [ ] Não coloque diretamente dentro de `templates/`, mas coloque dentro de `templates/app_name/`
  * - [ ] Garanta que podem ser alterados carregando algum template personalizando com o mesmo caminho

- [ ] Providencie template tags para apresentar dados complexos
  * - [ ] Deixa apenas lógica de apresentação dentro de template tags, quebre o resto da lógica dentro de helpers
    * Por exemplo, django-avatar tem um `avatar` template tag para gerar tags `img`, mas a lógica para gerar URLs avatar é [isolado em `providers.py`](https://github.com/grantmcconnaughey/django-avatar/blob/master/avatar/providers.py)

- [ ] Providencie views padrão
  * - [ ] Não quebre a configurabilidade dos class-based views. Permita que os atributos e métodos existentes nas views do Django sejam sobrescritos.
  * - [ ] Quebre lógica de views em comum dentro de mixins

- [ ] Evite models built-in se possível
  * - [ ] Se você precisa tê-los, providencie um model abstrato e habilite sua aplicação de trabalhar com uma variedade de customizados concretos
    * Exemplos de implementação:
    [django-taggit custom tag model](https://django-taggit.readthedocs.io/en/latest/custom_tagging.html#custom-tag)
    [django-blog-zinnia custom entry model](http://docs.django-blog-zinnia.com/en/develop/how-to/extending_entry_model.html)
    [django-contrib-comments custom app](https://django-contrib-comments.readthedocs.io/en/latest/custom.html)
  * - [ ] Quebre partes comuns de models dentro de models abstratos
  * - [ ] Não use model mixins, use models abstratos
    * Cheque a razão disso em [StackOverflow answer](http://stackoverflow.com/a/25817237/145349)
  * - [ ] Quando usar Generic Foreign Keys, permita que eles sejam substituídos por FKs diretas
    * Exemplos de implementação:
    [django-guardian support of direct foreign keys](http://django-guardian.readthedocs.io/en/latest/userguide/performance.html#direct-foreign-keys)
    [django-taggit support of custom through model](https://django-taggit.readthedocs.io/en/latest/custom_tagging.html#custom-foreignkeys)

- [ ] Isole lógica de campos form dentro de form fields e widgets
  * Cheque a implementação em [django-recaptcha](https://github.com/praekelt/django-recaptcha)

- [ ] Isole e lógica de campos model dentro de model fields
  * Cheque a implementação em [django-hashid-field](https://github.com/nshafer/django-hashid-field)

- [ ] Isole lógica de query dentro de métodos queryset, como filter, update e delete

- [ ] Isole lógica de comportamente a nível de tabela, dentro de métodos manager, como lógica do create

- [ ] Isole lógica de validação dentro de validators

- [ ] Use context processors somente para lógicas globais

- [ ] Use middlewares somente para lógicas globais relacionados ao ciclo request-response ou current user

- [ ] Evite código spathetti nos signals

## Manutenção
- [ ] Seja transparente sobre bugs, especialmente problemas de segurança
  * - [ ] Adicione warnings de segurança no CHANGELOG. Certifique-se de que eles são analisáveis por [ferramentas de segurança](https://github.com/pyupio/safety)

- [ ] Não abandone o projeto, give it away
