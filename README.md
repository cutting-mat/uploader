# @cutting-mat/uploader

[![npm](https://img.shields.io/npm/v/@cutting-mat/uploader.svg)](https://www.npmjs.com/package/@cutting-mat/uploader) [![license](https://img.shields.io/github/license/cutting-mat/uploader.svg)]()

基于 ElementUI/ElementPlus，整合图片上传前压缩、上传前剪裁、IOS 图片方向自动校正、自定义文件类型的 Vue 上传组件

适用于 ElementPlus 的[Vue3 版本](https://github.com/cutting-mat/uploader-plus)

## Feature

- [x] 支持全局配置
- [x] 支持 v-model 受控模式
- [x] 图片上传前压缩
- [x] 图片上传前剪裁
- [x] 拍照方向自动校正(需开启压缩或剪裁)
- [x] 自定义 accept 类型集合

## Quick Start

1. NPM 安装

```js
npm i @cutting-mat/uploader -S

```

2. 安装插件

```js
import uploader from "@cutting-mat/uploader";
import uploadConfig from "@/upload.config";
Vue.use(uploader, uploadConfig); // 安装时传入的配置为全局配置
```

3. 使用组件

```html
<uploader :uploadMethod="(file, fileName) => {...}"> 点击上传 </uploader>
```

## Config

```js
/**
 * @cutting-mat/uploader 配置文件
 * 支持 el-upload 除请求相关（action, headers, data, name, with-credentials, http-request）以外的所有 Prop
 * 支持 el-upload 的所有 Method
 * 附 el-upload 文档: https://element.eleme.cn/#/zh-CN/component/upload
 *
 * 额外支持以下属性，均支持全局配置：

 * accept[String]:              允许上传的文件类型, 同el-upload, 额外支持自定义文件类型（见下方 quickType ）
 * v-model / value[Array]:      已上传文件数据, 同el-upload, default: []
 * beforeUpload[Function]:      上传文件之前的钩子，同el-upload
 * onExceed[Function]:          文件超出个数限制时的钩子, 同el-upload
 * limitSize[Number]:           允许上传的最大文件尺寸，默认 100 * 1024 * 1024（100M）
 * imgCompress[Boolean]:        开启图片上传前压缩, default: true
 * imgCompressOption[Object]:   图片压缩尺寸配置, default:
    {
        maxWidth: 1000,            // 最大宽度
        maxHeight: 1000,           // 最大高度
    }
 * imgCrop[Boolean]:            开启图片上传前剪裁, default: false
 * imgCropOption[Object]:       图片剪裁配置, 选项同 [fengyuanchen/compressorjs], default:
    {
        ratio: 1,               // 剪裁框宽高比
        minWidth: 0,            // 最小输出宽度
        minHeight: 0,           // 最小输出高度
        maxWidth: 1000,         // 最大输出宽度
        maxHeight: 1000,        // 最大输出高度
    }
 * uploadMethod[Function]:      上传处理方法, 接收两个参数（file/blob, fileName），default: 无
 * responseTransfer[Function]:  接口返回数据 与 fileList 数据格式转换函数, default: (response) => return response;
 * quickType[Object]:           自定义文件类型, default:
    {
        "t-image": [".jpg", ".jpeg", ".png", ".gif", ".bmp", ".webp"],
        "t-video": [".mp4", ".rmvb", ".avi", ".mov", ".3gp", ".webm"],
        "t-audio": [".wav", ".mp3", ".ogg", ".acc"],
        "t-word": [".docx", ".doc"],
        "t-excel": [".xlsx", ".xls"],
        "t-ppt": [".ppt", ".pptx"],
        "t-document": [".pdf", "t-word", "t-excel", "t-ppt"],
        "t-zip": [".zip", ".rar"],
    }

 * */
```
