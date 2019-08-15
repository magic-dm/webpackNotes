# Webpack关键路径整理

1. 获取配置参数并启动webpack：
  1. ./node_modules/webpack-cli/bin/cli.js 
    1. 关键点：
      1. compiler = webpack(options)
  2. ./node_modules/webpack/lib/webpack.js 
    1. 关键点：
      1. new compiler()
      1. compiler.run()
      1. new WebpackOptionsApply()
2. 依次调用生命周期上的钩子并创建Compilation
  1. ./node_modules/webpack/lib/Compiler.js
    1. 关键点：
      1. run()
      1. compile()
3. Compilation执行依次编译
  1. ./node_modules/webpack/lib/Compilation.js
    1. 关键点：
      1. new MainTemplate() 、new ChunkTemplate() ---> chunk的渲染模板
    2. 关键点：
      1. addEntry()
      1. buildModule() ---> 去构建module
      1. seal() ---> 去创建bundle
      1. createChunkAssets() ---> 用渲染模板生成文件，并收集为文件列表
  2. ./node_modules/webpack/lib/NormalModule.js
    1. 关键点：
      1. build() ---> 构建module
  3. ./node_modules/webpack/lib/Chunk.js
4. 将生成的文件列表写出到对应的路径下
  1. ./node_modules/webpack/lib/Compiler.js
    1. 关键点：
      1. emitAssets()
