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
### 2.泛型与keyof的结合使用
    interface Person {
        name:string,
        age:number,
        isMale: boolean
    }
    class Teacher {
        constructor(private info: Person){}
        getDetailInfo<T extends keyof Person>(key:T):Person[T]{
            return this.info[key]
        }
    }
    const teacher = new Teacher({
        name: 'zhangsan',
        age: 35,
        isMale: true
    })
    const info = teacher.getDetailInfo('name')  // 只能是name,age,isMale
    console.log(info)
