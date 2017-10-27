# Módulo para login com WSO2 para THF versão AngularJS

## Configuração do projeto

* Incluir no __index.html__ a tag __`<base href="/"/>`__ caso tenha path usar como o exemplo __`<base href="/totvseai-monitor"/>`__
``` html
<!DOCTYPE html>
<html ng-app="totvsApp">
<head>
    <title>TOTVS | Sample Menu HTML</title>

    <base href="/"/>

</head>
```

* Copiar arquivo __dist/totvs-wso2-login.min.js__ no diretório __js/libs/totvs-html-framework__ e incluir no __index.html__
``` html
<script type="text/javascript" src="js/libs/totvs-html-framework/totvs-wso2-login.min.js"></script>
<script type="text/javascript" src="js/libs/totvs-html-framework/totvs-html-framework.min.js"></script>
```

* Incluir o __[ngCookies](https://docs.angularjs.org/api/ngCookies)__ versão 1.3.20 no projeto. Exemplo com CDN:
``` html
	<script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/angularjs/1.3.20/angular-cookies.js"></script>
```

* Incluir o module __totvsWso2Login__ no __totvs-app.module.js__
``` js
angular
    .module('totvsApp', [
        'ngSanitize',
        'ui.router',
        'ui.mask',
        'ui.select',
        'totvsWso2Login',
        'totvsHtmlFramework',
        'totvsDesktop'
    ]);
```

* Incluir o __TotvsWso2OauthProvider__ no __totvs-app.config.js__
``` js
angular
    .module('totvsApp')
    .config(totvsAppConfig);

    totvsAppConfig.$inject = ['$httpProvider','TotvsI18nProvider', 'TotvsWso2OauthProvider'];
    
    function totvsAppConfig($httpProvider, TotvsI18nProvider, TotvsWso2OauthProvider) {

        TotvsWso2OauthProvider.configure(
            {
                baseUrl:'https://<host do WSO2>',
                clientId:'<consumer key do WSO2>'
            });
    }
```