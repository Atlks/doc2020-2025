Go 绘图



draw.Draw(dst, image.Rect(0, height/4, width/2, 3*height/4), images[0], image.Pt(0, 0), draw.Over) // 绘制第一幅图 draw.Draw(dst, image.Rect(width/2, height/4, width, 3*height/4), images[1], image.Pt(0, 0), draw.Over) // 绘制第二幅图


Draw 函数的参数如下：
dst: 绘图的画布，只能是 *image.RGBA 或 *image.Paletted 类型
r: dst 上绘图范围
src: 要在画布上绘制的图像
sp: src 的起始点，实际绘制的图像是img.SubImage(image.Rectangle{Min: sp, Max: src.Bounds().Max})。注意，src 为 SubImage 时，sp 应为 src.Bounds().Min
op: porter-duff 混合方式, 具体介绍可以看下面的微软的参考资料。image/draw 库提供了 draw.Src 和 draw.Over 两种混合方式
draw.Src: 将 src 覆盖在 dst 上
draw.Over: src 在上，dst 在下按照 alpha 值进行混合。在图片完全不透明时，draw.Over 与 draw.Src 没有区别

