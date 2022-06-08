# 常用编程技巧和代码规范总结

## 一、前言

> ​	April（四月） 是以我的猫咪命名的一个开源团队，创立初衷是为了孵化一些项目到社区，意味着后续也会接受来自其他代码贡献者的代码，但是如果代码贡献者的编程风格与 April 的不一致，会给代码阅读者和其他代码提交者造成不小的困扰. April 因此总结了这份编程风格指南, 使所有提交代码的人都能获知 April 的编程风格.



## 二、Java 编码规范

​	Java 编程规范主要以阿里巴巴代码规约为主 ( GitHub 无法预览 PDF，所以将 PDF 转为图片了，如果不习惯，可以 clone 本仓库，使用 typora 可以以 PDF 方式查看下面的文档)





<div style="width:100%;height:600px;overflow-x:auto;overflow-y:auto">
    <img src="https://github.com/april-projects/april-norm/blob/main/img/JavaDevelopmentManual(HuangshanEdition).png?raw=true" alt="image">
<div>



<embed id="pdfPlayer" src="https://cdn.mobaijun.com/pdf/JavaDevelopmentManual%28HuangshanEdition%29.pdf" type="application/pdf" width="100%" height="800" >


## 三、编程技巧（补充）

### 一、注释规范

* 禁用行尾注释
* 方法或常量，成员变量，禁单行注释，应使用文档注释
* 类注释模板

~~~java
/**
  *software：IntelliJ IDEA 2022.1
  *class name: ${NAME}
  *class description： ${END}
  *
  *@author (作者名称) ${DATE} ${TIME}
*/
~~~

* 枚举注释模板

~~~java
/**
  *software：IntelliJ IDEA 2022.1
  *enum name: ${NAME}
  *enum description： ${END}
  *
  *@author (作者名称) ${DATE} ${TIME}
*/
~~~

* 接口注释模板

~~~java
/**
  *software：IntelliJ IDEA 2022.1
  *interface name: ${NAME}
  *interface description： ${END}
  *接口描述： ${END}
  *
  *@author (作者名称) ${DATE} ${TIME}
*/
~~~

* 注解注释模板

~~~java
/**
  *software：IntelliJ IDEA 2022.1
  *annotation name: ${NAME}
  *annotation description： ${END}
  *
  *@author (作者名称) ${DATE} ${TIME}
*/
~~~



### 二、建表规范

* 遵循三大范式
* 复杂字段之间用 （_） 下划线相隔，如（create_time，user_name）
* 禁止使用外键关联
* 主键字段使用（bigint）类型，Java 对应类型使用 Long 类型
* 日期类型字段是 （datetime），Java对应 LocalDateTime 类型



### 三、查询规范

* 列表查询

> 所有的列表查询都需要添加排序，已最后添加的数据显示在第一列，以 bigint 类型作为排序字段，如（主键 id ）

* 操作集合尽量使用 stream 和 lambda 表达式,工具类地址（com.mobaijun.common.util.stream）



### 四、返回规范

> * 项目中定义了三个返回类，目录地址（com.mobaijun.common.result）
>   * AbstractTip<T> 泛型父类，返回值
>   * SuccessTip<T> 成功返回
>   * ErrorTip<T> 异常返回
> * 项目中返回只能在 controller 层进行操作，禁止在业务层（service）实行（AbstractTip/Success/Error）返回
> * 业务层如果需要异常处理，使用 throw new Exception("");



### 五、增删改查返回规范

  * 新增：返回 boolean 类型或 int 类型
  * 修改：返回 boolean 类型或 int 类型
  * 删除：返回 int 类型
  * 查询：返回 List<Entity> 类型或 Entity 类型
  * 批量：返回 int 类型



### 六、接口规范

  * 类定义信息为 @Api(tags = {"一级目录-二级目录-业务类型"}, description = "具体描述")
  * 查询使用：@GetMapping(value = "/${methodName}")
  * 新增使用：@PostMapping(value = "/${methodName}")
  * 修改使用：@PostMapping(value = "/${methodName}")
  * 单个删除：@DeleteMapping(value = "/${methodName}")
  * 批量删除：@DeleteMapping(value = "/${methodName}")

> 命名规则：
>
>  * 单个删除（singleDelete）
>  * 批量删除（batchDelete）
>  * 新增 （insert[Entity]）
>  * 修改 （update[Entity]）
>  * 查询 （select[Entity]List）



### 七、枚举定义规范

1. 枚举如果没有set方法，属性需要使用 final 定义；
2. 枚举每个字段需包含文档注释
3. 枚举属性全部定义为大写，多个单纯之间以下划线分割

~~~java
@Getter
@AllArgsConstructor
public enum NameType {
    /**
     * 名称
     */
    FACTORY_NAME("name");
    
    /**
     * 值
     */
    private final String value;
}
~~~



## 四、代码提交规范

​	主要以 GitMoji 规范为主，[gitmoji](https://gitmoji.carloscuesta.me/) 是一个标准化和解释在GitHub提交消息上使用 [emoji](https://gitmoji.carloscuesta.me/) 的倡议。 [gitmoji](https://gitmoji.carloscuesta.me/) 是一个开源项目，专门规定了在 `github` 提交代码时应当遵循的 `emoji `规范，在 `git commit`上使用 `emoji` 提供了一种简单的方法，仅通过查看所使用的表情符号来确定提交的目的或意图。



​	在执行 `git commit` 指令时使用 `emoji` 图标为本次提交添加一个特别的图标， 这个本次提交的记录很容易突出重点，或者说光看图标就知道本次提交的目的。这样就方便在日后查看历史提交日子记录中快速的查找到对于的提交版本。由于有很多不同的表情符号，表情库更新后，没有一个可以帮助更轻松地使用表情符号的中文表情库列表。



​	提交示例，图标地址[传送门](https://gitmoji.dev/)

![](https://github.com/april-projects/april-norm/blob/main/img/image-20220608102324028.png?raw=true)
