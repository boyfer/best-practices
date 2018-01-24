# best-practices - (Java / PostgreSQL / Spring / Hibernate)

* "To address these difficulties, we recommend using date/time types that contain both date and time when using time zones. We do not recommend using the type time with time zone (though it is supported by PostgreSQL for legacy applications and for compliance with the SQL standard)".

  - https://www.postgresql.org/docs/current/static/datatype-datetime.html#DATATYPE-TIMEZONES

  Further reading for date/time types:

  - http://blog.untrod.com/2016/08/actually-understanding-timezones-in-postgresql.html
  - http://phili.pe/posts/timestamps-and-time-zones-in-postgresql/

* Argon2 won the password hashing competitions, but due to Spring implementations we should stick to bcrypt for now. Argon2 might still need some time. Links below:

  - https://hynek.me/articles/storing-passwords/
  - https://security.stackexchange.com/questions/107337/reviews-of-argon2
  - https://docs.spring.io/spring-security/site/docs/5.0.0.RELEASE/api/org/springframework/security/crypto/bcrypt/BCryptPasswordEncoder.html
  - https://docs.spring.io/spring-security/site/docs/5.0.0.RELEASE/api/org/springframework/security/crypto/scrypt/SCryptPasswordEncoder.html

* Two great sql style guides (or naming conventions) are below. First one seems derived by PostgreSQL:

  - https://launchbylunch.com/posts/2014/Feb/16/sql-naming-conventions/
  - http://www.sqlstyle.guide/

* Latest stable version of Spring Boot (1.5.9) doesn't support Java 9. It will be supported with Spring Boot 2.0 but it's still in progress:

  - https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-with-Java-9

* "The @Transactional annotation is metadata that specifies that an interface, class, or method must have transactional semantics". It still needs to be tested to see if I use it correctly:

  - https://docs.spring.io/spring/docs/5.0.2.RELEASE/spring-framework-reference/data-access.html#transaction-declarative-attransactional-settings

* It seems that adding "created_at" and "updated_at" columns are still common in database design:

  - https://softwareengineering.stackexchange.com/questions/118489/does-it-make-sense-to-standardize-including-a-created-date-and-last-updated-date
  - https://stackoverflow.com/questions/38916063/add-timestamp-column-with-default-now-for-new-rows-only
  - https://x-team.com/blog/automatic-timestamps-with-postgresql/

* The most common starting points for JSON:

  - https://mvnrepository.com/artifact/org.json/json
  - https://github.com/FasterXML/jackson

* As soon as there are examples of simple codes (or codenames) as primary keys, I'm gonna go for it. Saves a lot of work/time in development and much more elegant. One of the links suggest that the terms is called abbreviated encoding or Celko's encoding. But there is one more thing. It should be kept as small as possible, 3 characters at most (for performance reasons.)

  - https://www.red-gate.com/simple-talk/sql/database-administration/five-simple-database-design-errors-you-should-avoid/
  - https://stackoverflow.com/questions/337503/whats-the-best-practice-for-primary-keys-in-tables
  - https://www.techrepublic.com/blog/10-things/10-tips-for-choosing-between-a-surrogate-and-natural-primary-key/
  - http://www.itprotoday.com/business-intelligence/surrogate-key-vs-natural-key
  - https://dba.stackexchange.com/questions/142825/what-are-the-best-practices-regarding-lookup-tables-in-relational-databases/142841#142841
  - https://stackoverflow.com/questions/4824024/how-important-are-lookup-tables/4824718#4824718
  - https://dba.stackexchange.com/questions/6108/should-every-table-have-a-single-field-surrogate-artificial-primary-key
   
* There is a consensus about RESTful APIs in the coomunity, except the API versioning. Here are links:

  - https://hackernoon.com/restful-api-designing-guidelines-the-best-practices-60e1d954e7c9
  - https://blog.mwaysolutions.com/2014/06/05/10-best-practices-for-better-restful-api/
  - https://www.snyxius.com/21-best-practices-designing-launching-restful-api/
  - http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api
  - https://github.com/RestCheatSheet/api-cheat-sheet#api-design-cheat-sheet
  - https://medium.com/@schneidenbach/restful-api-best-practices-and-common-pitfalls-7a83ba3763b5 (Also technical details here!)
  
  Further reading on REST:
  
  - http://www.restapitutorial.com/resources.html
  - https://github.com/RestCheatSheet

* The choice between UUID vs Auto Increment really depends on the application. Some people defend UUID, dismiss auto-increment and some people do the opposite. There is no consensus on this topic. Some argumentation here:

  - https://dba.stackexchange.com/questions/91669/primary-key-auto-increment-best-practices
  - https://softwareengineering.stackexchange.com/questions/328458/is-it-good-practice-to-always-have-an-autoincrement-integer-primary-key
  - https://stackoverflow.com/questions/404040/how-do-you-like-your-primary-keys
  - https://www.experts-exchange.com/questions/21308273/auto-increment-columns-and-best-practice.html
  - https://medium.com/@Mareks_082/auto-increment-keys-vs-uuid-a74d81f7476a
  - https://www.clever-cloud.com/blog/engineering/2015/05/20/why-auto-increment-is-a-terrible-idea/
  
* In my opinion, the choice between soft delete vs hard delete really depends on the column. If it is a user table, then yes. Soft delete makes a lot of sense. But if it is like a "record" column in "jogtracker" application then hard delete should be sufficient. There is no reason to store incorrect rows inserted by the user itself. There is a lot of debate as usual on this topic.

  - https://stackoverflow.com/questions/378331/physical-vs-logical-soft-delete-of-database-record (Second answer is great.)
  - http://abstraction.blog/2015/06/28/soft-vs-hard-delete (Nice comparison)
  - http://udidahan.com/2009/09/01/dont-delete-just-dont/ (Advocating soft delete)
  - http://jameshalsall.co.uk/posts/why-soft-deletes-are-evil-and-what-to-do-instead (Advocating hard delete)
  - https://www.thoughts-on-java.org/implement-soft-delete-hibernate/ (Soft delete Hibernate implementation - might be useful though)
  
* Packaging by features instead of layers is the common practice:

  - http://www.javapractices.com/topic/TopicAction.do?Id=205
  - https://hackernoon.com/package-by-features-not-layers-2d076df1964d
  - https://dzone.com/articles/package-your-classes-feature
  - http://tidyjava.com/package-feature-demanded/
  - https://stackoverflow.com/questions/11733267/is-package-by-feature-approach-good
  - https://softwareengineering.stackexchange.com/questions/351216/if-i-package-by-feature-but-have-many-homogeneous-classes-what-is-preferable
  
* This item is a note to self. Service methods shouldn't have the same name as dao methods. Ex: 
  - recordService.create
  - recordService.list
  - recordService.update
  - **recordService.getRecordById** => This is wrong
  - recordService.delete
  - **recordService.getReport** => This method can also be changed as "report"
  
  As you can see above "get" would be much more elegant instead of "getRecordById". Standard REST service endpoints should have standard method names. Same goes with "getReport".
  
* JSON properties should have camelCase as it is told in REST conventions. The below code sample from jogtracker is WRONG!

```
  @JsonProperty("id")
  private Integer recordId;

  @JsonProperty("user_id")
  private Integer userId;
	
  @JsonProperty("air_temp")
  private Double airTemp;
	
  @JsonProperty("rel_temp")
  private Double relTemp;	
```

* The recommended timestamp format is "yyyy-MM-dd HH:mm:SS+tz" (ISO 8601). Ex:

  - https://www.postgresql.org/docs/current/static/datatype-datetime.html#DATATYPE-DATETIME-INPUT

```
  2004-10-19 10:23:54+02
```

* DAO classes should be named as xxxRepository. I found this convention by coincidence while checking JHipster:

	- http://gist.asciidoctor.org/?github-mraible/jhipster4-demo//README.adoc
	
* I did some research on authentication methods in REST and a lot of developers seem to misunderstand the concepts such as OAuth and JWT. The only approach that has been agreed upon is OpenID Connect on top of OAuth 2.0. But I still think that it might be an architectural overkill because either I have to use a third-party identity provider for authentication or implement it by myself. HMAC seems a reasonable approach for machine-machine communicationin REST with API keys and API secrets.
