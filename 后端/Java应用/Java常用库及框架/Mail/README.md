# Mail

## 学习指南

目前如果是Java程序，建议直接使用spring boot的mail starter功能。

``` pom
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-mail</artifactId>
</dependency>
```

### 参考配置

application.yml

``` yml
spring:
  mail:
    host: smtp.126.com
    port: 25
    username: yourusername
    password: YOURPASSWORD
```

### 参考代码

#### 发送简单邮件

``` java

  @Autowired
  private JavaMailSender mailSender;

  /**
    * 简单文本邮件
    *
    * @param to      收件人
    * @param subject 主题
    * @param content 内容
    */
  @Override
  public void sendSimpleMail(String to, String subject, String content) {
      // 创建SimpleMailMessage对象
      SimpleMailMessage message = new SimpleMailMessage();
      // 邮件发送人
      message.setFrom("yourusername@126.com");
      // 邮件接收人
      message.setTo(to);
      // 邮件主题
      message.setSubject(subject);
      // 邮件内容
      message.setText(content);
      // 发送邮件
      mailSender.send(message);
  }
```

#### 发送html邮件

``` java

  @Autowired
  private JavaMailSender mailSender;

   /**
     * html邮件
     *
     * @param to      收件人
     * @param subject 主题
     * @param content 内容
     */
    @Override
    public void sendHtmlMail(String to, String subject, String content) {
        MimeMessage message = mailSender.createMimeMessage();
        MimeMessageHelper messageHelper;
        try {
            messageHelper = new MimeMessageHelper(message, true);
            message.setSubject(subject);
            // 邮件内容，html格式
            messageHelper.setText(content, true);
            // 邮件发送人
            messageHelper.setFrom("yourusername@126.com");
            // 邮件接收人,设置多个收件人地址
            messageHelper.setTo(to);
            // 发送
            mailSender.send(message);
            // 日志信息
            log.info("邮件已经发送。");
        } catch (Exception e) {
            log.error("发送邮件时发生异常！", e);
            throw new RuntimeException("发送邮件时发生异常");
        }
    }
```

### TLS参考配置

application.yml

``` yml
spring:
  mail:
    host: smtp.126.com
    port: 465
    username: yourusername@126.com
    password: YOURPASSWORD
    protocol: smtps
    properties:
      mail:
        smtp:
          auth: true
          starttls:
            enable: true
            required: true
```

### TLS参考代码

#### TLS发送简单邮件

代码和上面的一致。

#### TLS发送html邮件

代码和上面的一致。

#### 经验总结（填坑必看）

* 阿里云建议使用TLS发送，否则需要开25端口的申请，还不一定给过
  * 阿里的业务申请里的25端口解封
  * [使用SSL加密465端口发送邮件](https://help.aliyun.com/document_detail/60692.html)
* 我上面的TLS端口是网易邮箱126的端口，其他运营商可能有区别
* 服务器需要开端口
* TLS协议是smtps

# 参考文献

1. [JavaMail API](https://www.oracle.com/java/technologies/javamail.html)
2. [Spring Boot features: Sending Email](https://docs.spring.io/spring-boot/docs/2.0.3.RELEASE/reference/html/boot-features-email.html)
3. [SpringBoot邮件发送](https://blog.csdn.net/qq_43581790/article/details/124874862)
