---
ms.openlocfilehash: 9bdfcca2fd03e24a636be3340f5057dc3f39358e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032734"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Проверка подлинности. Замена типов Newtonsoft.Json

В ASP.NET Core 3.0 типы `Newtonsoft.Json`, которые использовались в API проверки подлинности, заменены на типы `System.Text.Json`. Базовое использование пакетов проверки подлинности остается неизменным, за исключением следующих случаев:

* классы, производные от поставщиков OAuth, например от [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers);
* расширенные реализации манипуляций с утверждениями.

Подробную информацию см. на странице [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105). Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Представленная версия

3.0

#### <a name="recommended-action"></a>Рекомендованное действие

В производных реализациях OAuth самым типичным вариантом является замена `JObject.Parse` на `JsonDocument.Parse` в переопределении `CreateTicketAsync`, как показано [здесь](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). Объект `JsonDocument` реализует интерфейс `IDisposable`.

В следующем списке перечислены известные изменения:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> превращается в `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`. Аналогичным образом изменяются все производные реализации `ClaimAction`;
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> заменяется на `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> заменяется на `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`.
- из <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> удален один старый конструктор, а во втором `JObject` заменено на `JsonElement`. Соответственно обновлены свойство `User` и метод `RunClaimActions`;
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> теперь принимает параметр с типом `JsonDocument` вместо `JObject`. Соответственно обновлено свойство `Response`. `OAuthTokenResponse` теперь является высвобождаемым, и его высвобождает `OAuthHandler`. Производные реализации OAuth, переопределяющие `ExchangeCodeAsync`, не должны высвобождать `JsonDocument` или `OAuthTokenResponse`;
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> стал `JsonDocument` вместо `JObject`;
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> стал `JsonElement` вместо `JObject`;
- Последний параметр метода [TwitterHandler.CreateTicketAsync(ClaimsIdentity,AuthenticationProperties,AccessToken,JObject)](/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) изменен с `JObject` на `JsonElement`. Заменяющий метод — <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType>.

#### <a name="category"></a>Категория

ASP.NET Core

#### <a name="affected-apis"></a>Затронутые API

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
