---
layout: cover
---


# 组件 Props 类型声明

---

# props 声明规范
类型定义统一使用 type

类型定义统一放在组件的上方并导出

类型定义使用 大驼峰命名法 + `Props`作为后缀
```ts
export type PrimaryButtonProps = {
  children: React.ReactNode;
}

const PrimaryButton: React.FC<PrimaryButtonProps> = (props) => {
  return (
    <button className={styles.primaryButton} {...props}>
      {props.children}
    </button>
  );
};
export default PrimaryButton;
```
---

# 常见属性类型
```ts
type StudentModalProps = {
  name: string;
  age: number;
  isMale: boolean;
  hobbies: string[];
  address: {
    province: string;
    city: string;
  };
  onChange: (value: string) => void;
  onClose: () => void;
  style: React.CSSProperties;
  footer: React.ReactNode;
  labelProps?: LabelProps; // 可选属性
};
```

---

# 回调函数类型的属性
使用 on 或 handle 前缀，例如：onSubmit、handleClick 等

```ts
type StudentModalProps = {
  onClick: (value:string) => void;
  onSubmit: (value:string) => void;
  onClose: () => void;
}
```
---

# 可选属性
应该使用`?`标识,并设定默认值，减少入参

```ts
type StudentModalProps = {
  isNew?: boolean;   //false
  type?: 'add' | 'edit';  // 'add'
  onClick?: (value:string) => void; //() => {}
  footer?: React.ReactNode; // null
}
```
---

# 需要考虑支持组件的拓展
使用`React.ReactNode`标识

```ts
interface ReactElement<P = any, T extends string | JSXElementConstructor<any> = string | JSXElementConstructor<any>> {
    type: T;
    props: P;
    key: Key | null;
}
type ReactText = string | number;
type ReactChild = ReactElement | ReactText;

interface ReactPortal extends ReactElement {
    key: Key | null;
    children: ReactNode;
}

type ReactFragment = {} | Iterable<ReactNode>;
type ReactNode = ReactChild | ReactFragment | ReactPortal | boolean | null | undefined;
```