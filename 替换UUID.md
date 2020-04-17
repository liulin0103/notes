#  替换UUID

1. 复制common/data项目下的 UUID，UUIDUtils，UUIDs 拷贝到新项目对应目录下。

2. EntityId 接口增加一个 java.util.UUID getJavaUUID(); 接口

3. UUIDBased抽象类实现 java.util.UUID getJavaUUID() 接口

   ```java
       public java.util.UUID getJavaUUID() {
           return id.toJavaUUID();
       }
   ```

4. 全局替换  

   ```java
   import java.util.UUID;
   ```

    -> 

   ```java
   import com.lumi.saas.mc.common.data.id.UUID;
   ```

5. 全局替换 

   ```java
   import java.util.*;
   ```

    -> 

   ```java
   import com.lumi.saas.mc.common.data.id.UUID;
   import java.util.*;
   ```

6. Cassandra相关类使用

   ```java
   toJavaUUID();
   UUID.fromJavaUUID(java.util.UUID uuid);
   ```

   等方法解决转换的问题

7. dao项目下Cassandra相关类使用

   `EntityId.getJavaUUID();`方法替换`EntityId.getId();`解决因为类型不同引起的错误