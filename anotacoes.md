Entidade REVINFO
=========================

* Tabela global (para todas as entidades)
* Possui por padrão os campos id e timestamp
* Podem ser criados campos adicionais com a anotação *RevisionEntity* e um *listener* deve ser adicionado para preencher esses campos adicionais.   Veja [AuditedEntity](svexample-web/src/main/java/pl/pawelb/svexample/ds/AuditedEntity.java).
* Veja outras propriedades de configuração em http://docs.jboss.org/envers/docs/#configuration na tabela 3.1.

Entidade AUDITADA
=========================
* Anotar a classe com *@Audited* audita todas as propriedades, mas também é possível anotar somente as propriedades desejadas.
* Para cada CUD (Create, Update, Delete) é criada uma revisão na tabela com mesmo nome e sufixo _AUD (o qual pode ser alterado nas propriedades de configuração), os campos auditados e dois campos de controle chamados REV (Associado a revisão da tabela *REVINFO*) e REVTYPE, onde 0 = Create, 1 = Update e 2 DELETE.

Acessando uma revisão
=========================
A classe *AuditReader* provê um método para acessar uma determinada revisão conforme exemplo abaixo.
```java
AuditReader reader = AuditReaderFactory.get(entityManager);
Person oldPerson = reader.find(Person.class, personId, revision)
```
Também é possível executar queries mais complexas.
Veja http://docs.jboss.org/envers/docs/#queries.


> Written with [StackEdit](https://stackedit.io/).