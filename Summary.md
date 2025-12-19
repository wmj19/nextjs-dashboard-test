## Chapter 01 Getting Stared
## Chapter 02 CSS Styling
## Chapter 03 Optimizing Fonts and Images
- next/font ==> 防止布局偏移
- next/image ==> 使用`<Image />`标签来代替`<img />`标签
## Chapter 04 Creating Layouts and Pages
- 文件夹名字即为route
- layout.tsx和page.tsx的使用
## Chapter 05 Navigating Between Pages
- next/link ==> 使用`<Link></Link>`标签代替`<a></a>`
- clsx库的使用
## Chapter 06 Setting Up Your Database
- 使用vercel提供的数据库服务
## Chapter 07 Fetching Data
- 使用postgres库进行sql查询等操作
- 什么是request waterfalls请求瀑布流
  > 就是几个request按顺序执行，第二个request必须等待第一个request完成后才能发起，第三个request必须等待第二个request完成后才能发起... 但是并不是说这样的请求就是差劲的，如果后续的数据依赖前者的数据，那还是要使用这种方式的
- 什么是Parallel request
  > 使用了Promise.all/Promise.allSelected(),同时发送请求，同时结束，假设有3个request，第一个请求request需要10秒，第二个request只需要2秒，第三个request只需要5秒，那么就算第二个请求request已经获取到数据，也要等10秒后才能完成

## Chapter 08 Static and Dynamic Rendering
- Static Rendering是什么
- Dynamic Rendering是什么
## Chapter 09 Streaming
- Streaming允许拆成小块来请求，也就是说一个页面假如油3个request，分别需要10秒，2秒，5秒，那么可以让请求到数据后不必等待别的request，直接返回
- 使用`<Suspense></Suspense>`标签实现
  > import { Suspense } from 'react';fallback={....}可以作为备用组件来显示

最佳实践：将数据获取下移到需要它的组件，然后使用Suspense包装这些组件

## Chapter 10 Adding Search and Pagination
- import { useSearchParams, usePathname, useRouter } from 'next/navigation';
- Debouncing防抖：
  > 延迟进行某项操作,达到设定好的条件再进行某项操作,可以使用第三方库use-debounce实现，也可以手动实现
## Chapter 11 Mutating Data
- Server Action 可以利用异步方法直接获取数据
- 'use server'
- 在`<form actions={....}></form>`，大括号里的值建议统一写函数名，否则会直接触发一次，会导致需要参数的表单出错
  ```javascript
  const bindUseMethodName = useMethodName.bind(null, ...);
 
  return <form action={bindUseMethodName}>{/* ... */}</form>;
  // 这也是最佳实践之一
  ```
- next/cache ==> revalidatePath清除缓存
- 'next/navigation' ==> redirect重定向到哪个页面
- import { z } from 'zod';用于TypeScript验证类型的第三方库
- `[]`文件夹的名字带有方括号，那这个页面就是动态路由的页面
## Chapter 12 Handling Errors
- error.tsx 当出错是跳转到这个组件
- not-found.tsx ==> `import { notFound } from 'next/navigation';`
## Chapter 13 Improving Accessibility
- `pnpm add -D eslint eslint-config-next`使用eslint这个插件来帮助检查代码的accessibility
- 表单验证
  - Client-Side验证
  - Server-Side验证
    - react中useActionState的使用
## Chapter 14 Adding Authentication
- 说白了就是登陆功能的实现，`NextAuth.js的使用`
- Authentication --> 验证你的身份； Authorization --> 决定你能访问哪些内容
## Chapter 15 Adding Metadata
- 在dev tools中可以看到的`<title></tilte>, <meta></meta>...`标签和内容
- 可以帮助搜索引擎进行检索
- `import { Metadata } from 'next';`的使用