# Spring Boot Redis Example 

  The point of this project was to given an example of how to configure Redis  with Spring Boot. I have provided
a Java Configuration class for the Redis Beans. Also in the example there is a simple CRUD api provided that is based
on REDIS as the DAO.


	@Bean
    public RedisTemplate<String, User> redisTemplate() {
        RedisTemplate<String, User> redisTemplate = new RedisTemplate<>();
        redisTemplate.setConnectionFactory(jedisConnFactory);
        redisTemplate.setKeySerializer(stringRedisSerializer());
        redisTemplate.setValueSerializer(jacksonJsonRedisJsonSerializer());
        return redisTemplate;
    }
    
  Above is an example of a bean created for the RedisTemplate class to return back Java Serialized objects as a User a class. We have provided the connection Factory, Key Serializer and a the value Serializer. We have created both beans for the KeySerializer and the Value Serializer. These are show below.
  
  	@Bean
    public StringRedisSerializer stringRedisSerializer() {
        StringRedisSerializer stringRedisSerializer = new StringRedisSerializer();
        return stringRedisSerializer;
    }

    @Bean
    public JacksonJsonRedisSerializer<User> jacksonJsonRedisJsonSerializer() {
        JacksonJsonRedisSerializer<User> jacksonJsonRedisJsonSerializer = new JacksonJsonRedisSerializer<>(User.class);
        return jacksonJsonRedisJsonSerializer;
    }
