# SpringBoot

## 学习指南

### 核心资料

### 普通资料

### 学习步骤

## 知识点

* 启动时生成pid文件
  * 用来明确生成了那个进程，可以用脚本关闭进程，文件名称application.pid

``` java
    public static void main(String[] args) {
        log.info("start");
        SpringApplication app = new SpringApplication(WordApplication.class);
        app.addListeners(new ApplicationPidFileWriter());
        app.run(args);
    }
```

## 项目实战

## 参考文献
