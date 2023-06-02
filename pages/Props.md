---
layout: center
---


# Props Type

---

# 组件的 props 类型定义统一使用 type

```ts
type PrimaryButtonProps = {
  children: React.ReactNode;
}

const PrimaryButton: React.FC<PrimaryButtonProps> = (props) => {
  return (
    <button className={styles.primaryButton} {...props}>
      {props.children}
    </button>
  );
};
```
---

# props 类型定义统一放在组件的上方并导出

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

# props 命名规范
使用 大驼峰命名法 + `Props`作为后缀

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
  onClick?: (value:string) => void;
  onSubmit?: (value:string) => void;
  isNew?: boolean;
}
```
---

# 接受组件的属性
使用`React.ReactNode`标识

```ts
type TableProps = {
  footer: React.ReactNode;
}

```