# BlueOS 动态壁纸表盘 · Galaxy Lounge

基于 vivo 蓝河操作系统(BlueOS)的手表表盘项目,将 Wallpaper Engine 壁纸 **「Galaxy Lounge 4K」** 做成动态表盘。

## 效果

- 表盘主体为动态壁纸:从原视频截取 5 秒(466×466,10fps,共 50 帧 JPEG),由帧序列动画循环播放
- 适配圆形手表(466×466)与方形手表(watch-square),圆表按圆形容器裁剪
- 静态壁纸作为兜底底图,帧加载前不黑屏
- 表盘 id:`3001`,入口组件 `src/watch3001/index.ux`

## 开发与预览

1. 安装 [BlueOS Studio](https://blueos.vivo.com/develop)(注意:项目路径必须全英文);
2. 用 BlueOS Studio 打开本仓库根目录;
3. 打开 `src/watch3001/index.ux`,点击预览图标即可在模拟器实时预览;
4. 顶部工具栏「打包」可生成 rpk 安装包(debug 免签名,release 需签名)。

## 目录结构

```
src/
├── manifest.json          # 应用配置(包名、设备类型、表盘注册)
├── app.ux                 # 空占位(表盘模式不加载)
└── watch3001/
    ├── index.ux           # 表盘主体(帧序列动画逻辑)
    ├── edit.ux            # 长按编辑页(占位)
    └── assets/
        ├── 3001.png       # 表盘预览图
        ├── wallpaper.jpg  # 静态兜底壁纸
        └── frames/        # 50 帧动画帧(frame_001 ~ frame_050)
```

## 自定义

- 换片段 / 帧率 / 质量:用 ffmpeg 重新生成 `assets/frames/` 下的帧,并同步修改 `index.ux` 中的 `FRAME_COUNT`;
- 帧率由 `FRAME_MS`(毫秒)控制,当前 100ms(10fps)。

## 素材来源与版权

动态壁纸截取自 Wallpaper Engine 创意工坊作品 [Galaxy Lounge 4K](https://steamcommunity.com/app/431960/workshop/),仅供个人学习研究使用,**请勿商用**;分发前请自行获得原作者授权。
