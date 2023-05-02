# 1-service-management

Para reproduzir a questão:

- Criar projeto no Openshift
oc new-project tellyme

- Deployment dos projetos (pasta depoyment)
oc apply -f .
oc expose svc api
oc get route
curl http://api-tellyme.apps.cluster-zfn52.zfn52.sandbox1811.opentlc.com/api/list
* A host pode mudar de acordo com seu ambiente 

- Chegar se o Service Mesh está habilitado para o projeto:

- fazer patch no projeto istio-system, adicionando no service mesh member roll ou

- entrar no projeto tellyme, ir no operador, depois em Istio Service Mesh Member, e criar um novo, referenciando o control plane criado no projeto istio-system

- Criar gateway
- Criar o virtual service
- Criar o destination rule 

Testar a aplicação:

curl http://istio-ingressgateway-istio-system.apps.cluster-zfn52.zfn52.sandbox1811.opentlc.com/api/list

curl -H "end-user: redhatter" -s http://istio-ingressgateway-istio-system.apps.cluster-zfn52.zfn52.sandbox1811.opentlc.com/api/list