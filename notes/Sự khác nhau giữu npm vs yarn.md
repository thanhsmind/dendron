# Sự khác nhau giữu npm vs yarn

## npm và yarn là gì?
npm và yarn là 2 package manager phổ biết của jabascirpt. Có chứ năng tương tự nhau.

## Sự khác nhau giữa npm và yarn
### Tốc độ
- Npm: Chạy tuần tự 
- yarn: chạy parallel, và tự optimized fetch các packages liên quan
=> yarn chạy nhanh hơn npm

### Security
- NPM check security mỗi lần install
- **Security í one ò Yarn's core features**

### Ease of use
cả NPM và Yarn đều dễ sử dụng

## Basic Commands

**To see list of commands:**  
NPM - `npm`  
Yarn - `yarn`

**Install dependencies from package.json:**  
NPM - `npm install`  
Yarn - `yarn`

**Install a package and add to package.json:**  
NPM - `npm install package --save`  
Yarn - `yarn add package`

**Install a devDependency:**  
NPM - `npm install package --save-dev`  
Yarn - `yarn add package --dev`

**Remove a dependency:**  
NPM - `npm uninstall package --save`  
Yarn - `yarn remove package`

**Upgrade a package to its latest version:**  
NPM - `npm update --save`  
Yarn - `yarn upgrade`

**Install a package globally:**  
NPM - `npm install package -g`  
Yarn - `yarn global add package`