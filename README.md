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
