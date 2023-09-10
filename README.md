# _web-services-REST-asynchrone_
## Objectifs
Création d'un web services REST asynchrone en utilisant Talend ESB.

## Outils et Versions
- Talend Open Studio for ESB Version: 8.0.1
- Java Version 11
- SOAPUI Version Lastes

## Service Web REST asynchrone
> Un service web REST asynchrone est un service web basé sur l'architecture REST qui permet à un client d'envoyer une demande au serveur, puis de continuer à fonctionner sans attendre une réponse immédiate. 
> Le serveur traitera la demande en arrière-plan et fournira la réponse ultérieurement lorsque le traitement sera terminé. 
> Cela permet de gérer efficacement des opérations longues ou intensives en ressources sans bloquer le client.

## Création Web REST asynchrone
cette exemple affiche les fields du document json poster dans le service apres 5 secondes s'il n'y a pas eu un probléme d'extraction sinon il affiche l'erreur apres 10 secondes.
![Création Web REST asynchrone.](/image/ws_async_exemple.PNG "Exemple de création Web REST asynchrone.")

| Composants | Configuration |
| ------ | ------ |
| Configuration du composant tRESTRequest_1 | ![Création Web REST asynchrone.](/image/config-tRESTRequest_1.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tSetGlobalVar_1 | ![Création Web REST asynchrone.](/image/config-tSetGlobalVar_1.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tRESTResponse_1 | ![Création Web REST asynchrone.](/image/config-tRESTResponse_1.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tFixedFlowInput_1 | ![Création Web REST asynchrone.](/image/config-tFixedFlowInput_1.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tExtractJSONFields_1 | ![Création Web REST asynchrone.](/image/config-tExtractJSONFields_1.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tSleep_1 | ![Création Web REST asynchrone.](/image/config-tSleep_1.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tLogRow_1 | ![Création Web REST asynchrone.](/image/config-tLogRow_1.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tSleep_2 | ![Création Web REST asynchrone.](/image/config-tSleep_2.PNG "Exemple de création Web REST asynchrone.") |
| Configuration du composant tLogRow_2 | ![Création Web REST asynchrone.](/image/config-tLogRow_2.PNG "Exemple de création Web REST asynchrone.") |

## Test Web REST asynchrone

Lancer le Service en local (sur le studio Talend ESB)
![Test Web REST asynchrone.](/image/exec_service_local.PNG "Test Web REST asynchrone.")

Il est possible de tester votre service REST avec SOAPUI.

- Lancer SOAPUI
- Cliquer sur l'icône REST en haut de la fenêtre principale
- Entrer l'URI que vous désirez tester: http://localhost:8088/users?from=2&to=4
![Test Web REST asynchrone.](/image/creation-ws-REST-SOAPUI.PNG "Test Web REST asynchrone.")
- La fenêtre suivante devrait apparaître:
![Test Web REST asynchrone.](/image/creation-ws-REST-SOAPUI1.PNG "Test Web REST asynchrone.")

- Ajouter dans la request le JSON suivant :
```
{
	"message":"Test Web Service REST",
	"status":"OK"
}
```
- Cliquer sur la flèche verte. Le résultat devra ressembler au suivant, le resultat sera toujours "#status#	HTTP/1.1 202 Accepted":
![Test Web REST asynchrone.](/image/resultat-SOAPUI.PNG "Test Web REST asynchrone.")

Lorsqu'on retourne sur le Talend 
![Test Web REST asynchrone.](/image/result-ws_async_exemple.PNG "Test Web REST asynchrone.")
