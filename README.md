# SwiftDrawDemo
### 11月28日练习
* 思路参考自：[swift3.0 CoreGraphics绘图-实现画板](http://www.cnblogs.com/gongxiaokai/p/7123816.html)
* 创建一个DrawView类，重写draw方法：
```
    override func draw(_ rect: CGRect) {
        super.draw(rect)
        
        let context = UIGraphicsGetCurrentContext()
        context?.setLineCap(.round)
        context?.setLineJoin(.round)
        
        if allLines.count > 0 {
            for i in 0..<allLines.count {
                let linePoints = allLines[i]
                if linePoints.count > 0 {
                    context?.beginPath()
                    context?.move(to: linePoints[0])
                    for j in 0..<linePoints.count {
                        context?.addLine(to: linePoints[j])
                    }
                    context?.setLineWidth(self.lineWidth)
                    context?.setStrokeColor(strokeColors[i])
                    context?.strokePath()
                }
            }
        }
        if currentPoints.count > 0 {
            context?.beginPath()
            context?.setLineWidth(self.lineWidth)
            context?.setStrokeColor(self.strokeColor.cgColor)
            context?.move(to: currentPoints[0])
            for i in 0..<currentPoints.count {
                context?.addLine(to: currentPoints[i])
            }
            context?.strokePath()
        }
    }
```
