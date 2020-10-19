# slef-vue-plugin
简介：
自己项目用过的vue组件

注意：
1、图片上传和富文本属于vue+iview 使用时注意标签的使用
2、cropperJs为图片裁剪
3、pdfjs为PDF预览器插件。用法：把整个文件部署到网站目录，指向web/viewer.html?file=您的文件路径
	例子：
	let pdfInfoServerUrl = 'https://www.swap.fish/pdfjs/web/viewer.html'
	let pdfUrl = 'https://www.swap.fish/course.pdf' // 调取接口返回文件流
	let ifameURL = `${pdfInfoServerUrl}?file=${pdfUrl}`
	<iframe src={ifameURL} width="100%" height="100%" ></iframe>
