NSURLSessionEffectiveConfiguration - _socketStreamProperties is a connection property
(lldb) expr className
Realm was compiled with optimization - stepping may behave oddly; variables may not be available.
(__NSCFString *) $0 = 0x0000600002169600 @"RealmSwiftPermissionRole"
(lldb) expr objectClass
error: Couldn't materialize: couldn't get the value of variable objectClass: variable not available
error: errored out in DoExecute, couldn't PrepareToExecuteJITExpression
(lldb) up
frame #2: 0x0000000109873480 Realm`RLMRegisterClass(cls=RealmSwiftPermissionRole) at RLMSchema.mm:84:31 [opt]
   81  	
   82  	    auto prevState = s_sharedSchemaState;
   83  	    s_sharedSchemaState = SharedSchemaState::Initializing;
-> 84  	    RLMObjectSchema *schema = [RLMObjectSchema schemaForObjectClass:cls];
    	                              ^
   85  	    s_sharedSchemaState = prevState;
   86  	
   87  	    // set unmanaged class on shared shema for unmanaged object creation
(lldb) up
frame #3: 0x0000000109873cef Realm`::__25+[RLMSchema sharedSchema]_block_invoke(.block_descriptor=<unavailable>, (null)=<unavailable>, cls=<unavailable>, (null)=<unavailable>) at RLMSchema.mm:265:17 [opt]
   262 	            }
   263 	
   264 	            [s_localNameToClass enumerateKeysAndObjectsUsingBlock:^(NSString *, Class cls, BOOL *) {
-> 265 	                RLMRegisterClass(cls);
    	                ^
   266 	            }];
   267 	        }
   268 	        catch (...) {
(lldb) up
frame #4: 0x000000010a588277 CoreFoundation`__NSDICTIONARY_IS_CALLING_OUT_TO_A_BLOCK__ + 7
CoreFoundation`__NSDICTIONARY_IS_CALLING_OUT_TO_A_BLOCK__:
->  0x10a588277 <+7>: popq   %rbp
    0x10a588278 <+8>: retq   
    0x10a588279 <+9>: nopl   (%rax)

CoreFoundation`__NSDictionaryParameterCheckIterate:
    0x10a588280 <+0>: testq  %rdx, %rdx
(lldb) up
frame #5: 0x000000010a562fde CoreFoundation`-[__NSDictionaryM enumerateKeysAndObjectsWithOptions:usingBlock:] + 238
CoreFoundation`-[__NSDictionaryM enumerateKeysAndObjectsWithOptions:usingBlock:]:
->  0x10a562fde <+238>: movq   %r12, %rdi
    0x10a562fe1 <+241>: callq  0x10a522430               ; _CFAutoreleasePoolPop
    0x10a562fe6 <+246>: cmpb   $0x0, -0x90(%rbp)
    0x10a562fed <+253>: jne    0x10a563087               ; <+407>
(lldb) up
frame #6: 0x0000000109873b6b Realm`::+[RLMSchema sharedSchema](self=RLMSchema, _cmd=<unavailable>) at RLMSchema.mm:264:13 [opt]
   261 	                RLMRegisterClassLocalNames(classes.get(), numClasses);
   262 	            }
   263 	
-> 264 	            [s_localNameToClass enumerateKeysAndObjectsUsingBlock:^(NSString *, Class cls, BOOL *) {
    	            ^
   265 	                RLMRegisterClass(cls);
   266 	            }];
   267 	        }
(lldb) expr cls
error: use of undeclared identifier 'cls'
(lldb) down
frame #5: 0x000000010a562fde CoreFoundation`-[__NSDictionaryM enumerateKeysAndObjectsWithOptions:usingBlock:] + 238
CoreFoundation`-[__NSDictionaryM enumerateKeysAndObjectsWithOptions:usingBlock:]:
->  0x10a562fde <+238>: movq   %r12, %rdi
    0x10a562fe1 <+241>: callq  0x10a522430               ; _CFAutoreleasePoolPop
    0x10a562fe6 <+246>: cmpb   $0x0, -0x90(%rbp)
    0x10a562fed <+253>: jne    0x10a563087               ; <+407>
(lldb) down
frame #4: 0x000000010a588277 CoreFoundation`__NSDICTIONARY_IS_CALLING_OUT_TO_A_BLOCK__ + 7
CoreFoundation`__NSDICTIONARY_IS_CALLING_OUT_TO_A_BLOCK__:
->  0x10a588277 <+7>: popq   %rbp
    0x10a588278 <+8>: retq   
    0x10a588279 <+9>: nopl   (%rax)

CoreFoundation`__NSDictionaryParameterCheckIterate:
    0x10a588280 <+0>: testq  %rdx, %rdx
frame #3: 0x0000000109873cef Realm`::__25+[RLMSchema sharedSchema]_block_invoke(.block_descriptor=<unavailable>, (null)=<unavailable>, cls=<unavailable>, (null)=<unavailable>) at RLMSchema.mm:265:17 [opt]
   262 	            }
   263 	
   264 	            [s_localNameToClass enumerateKeysAndObjectsUsingBlock:^(NSString *, Class cls, BOOL *) {
-> 265 	                RLMRegisterClass(cls);
    	                ^
   266 	            }];
   267 	        }
   268 	        catch (...) {
(lldb) expr cls
error: Couldn't materialize: couldn't get the value of variable cls: variable not available
error: errored out in DoExecute, couldn't PrepareToExecuteJITExpression
(lldb) down
frame #2: 0x0000000109873480 Realm`RLMRegisterClass(cls=RealmSwiftPermissionRole) at RLMSchema.mm:84:31 [opt]
   81  	
   82  	    auto prevState = s_sharedSchemaState;
   83  	    s_sharedSchemaState = SharedSchemaState::Initializing;
-> 84  	    RLMObjectSchema *schema = [RLMObjectSchema schemaForObjectClass:cls];
    	                              ^
   85  	    s_sharedSchemaState = prevState;
   86  	
   87  	    // set unmanaged class on shared shema for unmanaged object creation
(lldb) expr cls
(Class) $1 = RealmSwiftPermissionRole
(lldb) expr cls.name
error: member reference base type 'Class' is not a structure or union
(lldb) down
frame #1: 0x000000010980adbe Realm`::+[RLMObjectSchema schemaForObjectClass:](self=<unavailable>, _cmd=<unavailable>, objectClass=<unavailable>) at RLMObjectSchema.mm:164:13 [opt]
   161 	        }
   162 	
   163 	        if (!schema.primaryKeyProperty) {
-> 164 	            @throw RLMException(@"Primary key property '%@' does not exist on object '%@'", primaryKey, className);
    	            ^
   165 	        }
   166 	        if (schema.primaryKeyProperty.type != RLMPropertyTypeInt && schema.primaryKeyProperty.type != RLMPropertyTypeString) {
   167 	            @throw RLMException(@"Property '%@' cannot be made the primary key of '%@' because it is not a 'string' or 'int' property.",
(lldb) up
frame #2: 0x0000000109873480 Realm`RLMRegisterClass(cls=RealmSwiftPermissionRole) at RLMSchema.mm:84:31 [opt]
   81  	
   82  	    auto prevState = s_sharedSchemaState;
   83  	    s_sharedSchemaState = SharedSchemaState::Initializing;
-> 84  	    RLMObjectSchema *schema = [RLMObjectSchema schemaForObjectClass:cls];
    	                              ^
   85  	    s_sharedSchemaState = prevState;
   86  	
   87  	    // set unmanaged class on shared shema for unmanaged object creation
(lldb) down
frame #1: 0x000000010980adbe Realm`::+[RLMObjectSchema schemaForObjectClass:](self=<unavailable>, _cmd=<unavailable>, objectClass=<unavailable>) at RLMObjectSchema.mm:164:13 [opt]
   161 	        }
   162 	
   163 	        if (!schema.primaryKeyProperty) {
-> 164 	            @throw RLMException(@"Primary key property '%@' does not exist on object '%@'", primaryKey, className);
    	            ^
   165 	        }
   166 	        if (schema.primaryKeyProperty.type != RLMPropertyTypeInt && schema.primaryKeyProperty.type != RLMPropertyTypeString) {
   167 	            @throw RLMException(@"Property '%@' cannot be made the primary key of '%@' because it is not a 'string' or 'int' property.",
(lldb) e
Enter expressions, then terminate with an empty line to evaluate:
1 
(lldb) e primaryKey
error: Couldn't materialize: couldn't get the value of variable primaryKey: no location, value may have been optimized out
error: errored out in DoExecute, couldn't PrepareToExecuteJITExpression
(lldb) up
frame #2: 0x0000000109873480 Realm`RLMRegisterClass(cls=RealmSwiftPermissionRole) at RLMSchema.mm:84:31 [opt]
   81  	
   82  	    auto prevState = s_sharedSchemaState;
   83  	    s_sharedSchemaState = SharedSchemaState::Initializing;
-> 84  	    RLMObjectSchema *schema = [RLMObjectSchema schemaForObjectClass:cls];
    	                              ^
   85  	    s_sharedSchemaState = prevState;
   86  	
   87  	    // set unmanaged class on shared shema for unmanaged object creation
(lldb) fr v class
error: no variable named 'class' found in this frame
(lldb) fr v class
error: no variable named 'class' found in this frame
(lldb) fr v cls
(Class) cls = RealmSwiftPermissionRole
(lldb) down
frame #1: 0x000000010980adbe Realm`::+[RLMObjectSchema schemaForObjectClass:](self=<unavailable>, _cmd=<unavailable>, objectClass=<unavailable>) at RLMObjectSchema.mm:164:13 [opt]
   161 	        }
   162 	        
   163 	        if (!schema.primaryKeyProperty) {
-> 164 	            @throw RLMException(@"Primary key property '%@' does not exist on object '%@'", primaryKey, className);
    	            ^
   165 	        }
   166 	        if (schema.primaryKeyProperty.type != RLMPropertyTypeInt && schema.primaryKeyProperty.type != RLMPropertyTypeString) {
   167 	            @throw RLMException(@"Property '%@' cannot be made the primary key of '%@' because it is not a 'string' or 'int' property.",
(lldb) 