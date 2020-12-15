### Typescript

### 1.函数声明与函数表达式
    函数声明：   function sum(x: number, y: number): number { return x + y; }
    函数表达式： let mySum: (x: number, y: number) => number = function (x: number, y: number): number { return x + y; }
    在 TypeScript 的类型定义中，=> 用来表示函数的定义，左边是输入类型，需要用括号括起来，右边是输出类型
    用接口定义函数的形状：
    interface SearchFunc {
      (source: string, subString: string): boolean;
    }
    let mySearch: SearchFunc = function(source: string, subString: string) {
        return source.search(subString) !== -1;
    }
