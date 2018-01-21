# best-practices - (Java / PostgreSQL / Spring / Hibernate)

* "To address these difficulties, we recommend using date/time types that contain both date and time when using time zones. We do not recommend using the type time with time zone (though it is supported by PostgreSQL for legacy applications and for compliance with the SQL standard)".
https://www.postgresql.org/docs/current/static/datatype-datetime.html#DATATYPE-TIMEZONES

Further reading for date/time types:
http://blog.untrod.com/2016/08/actually-understanding-timezones-in-postgresql.html
http://phili.pe/posts/timestamps-and-time-zones-in-postgresql/

* Argon2 won the password hashing competitions, but due to Spring implementations we should stick to bcrypt for now. Argon2 might still need some time. Links below:

https://hynek.me/articles/storing-passwords/
https://security.stackexchange.com/questions/107337/reviews-of-argon2
https://docs.spring.io/spring-security/site/docs/5.0.0.RELEASE/api/org/springframework/security/crypto/bcrypt/BCryptPasswordEncoder.html
https://docs.spring.io/spring-security/site/docs/5.0.0.RELEASE/api/org/springframework/security/crypto/scrypt/SCryptPasswordEncoder.html

* Two great sql style guides (or naming conventions) are below. First one seems derived by PostgreSQL:

https://launchbylunch.com/posts/2014/Feb/16/sql-naming-conventions/
http://www.sqlstyle.guide/
