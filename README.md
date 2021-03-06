# ReactUseState
## 工作原理
对于 useState Hook，考虑如下例子

```javascript
function App() {
  const [num, updateNum] = useState(0);
  return <p onClick={() => updateNum(num => num + 1)}>{num}</p>;
}
```

可以将工作分为两部分：
 1. 通过一些途径产生更新，更新会造成组件render。
 2. 组件render时useState返回的num为更新后的结果。
 
其中步骤1的更新可以分为mount和update：
 1. 调用ReactDOM.render会产生mount的更新，更新内容为useState的initialValue（即0）。
 2. 点击p标签触发updateNum会产生一次update的更新，更新内容为num => num + 1。