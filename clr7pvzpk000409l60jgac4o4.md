---
title: "Use aliases for your imports"
datePublished: Wed Jan 10 2024 11:48:35 GMT+0000 (Coordinated Universal Time)
cuid: clr7pvzpk000409l60jgac4o4
slug: use-aliases-for-your-imports
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/kyCNGGKCvyw/upload/3ba3a476f3bfbf622e7674387423d1a3.jpeg
tags: tutorial, frontend, angularjs, web-development, angular, webdev, typescript, frontend-development

---

In **TypeScript** projects, especially in **Angular**, it's easy to have too many files and too many imports in our components. This leads to confusion and errors when importing. In this post we have a quick guide to avoid this.

We've all seen this type of import in our files:

```typescript
import { Something } from '../../../../../../../something.ts';
```

You can work around this by using aliases in the `tsconfig.json` attribute via paths:

```typescript
// tsconfig.json
{
  "compilerOptions": {
    ...
    "paths": {
      "@components/*": ["src/app/components/*"],
      "@routes/*": ["src/app/routes/*"],
      "@shared/*": ["src/app/shared/*"],       
    }
  }
}
```

You can then use these aliases to import your resources:

```typescript
import { ButtonComponent, CardComponent } from '@components';
import { formatText } from '@shared/utils/formatting';
import { converting } from '@shared/utils/converting';
```

## Conclusion

You should do this for several reasons:

* It is much easier to read than relative paths.
    
* This is useful for refactoring: if your code changes location, the import stays the same.
    
* IDEs can import directly from aliases