总操作流程：
- 1、下载安装
- 2、写代码
- 3、测试

***

# 下载安装

```js
cnpm install --save file-saver xlsx 
```

# 写代码

>1、在有要导出table的组件中引用

```js
import XLSX from 'xlsx';
import FileSaver from 'file-saver'
```

>2、table的元素加id
```js
id="PSTableData"
```

>3、写方法
```js
exportExcel(val) { //导出Excel
        let wb=XLSX.utils.table_to_book(document.getElementById('PSTableData'));
        let wbout=XLSX.write(wb,{bookType:'xlsx',type:'binary'});
        FileSaver.saveAs(new Blob([this.s2ab(wbout)],{type:'application/octet-stream'}),"ProductionSchedule.xlsx");
      },
      s2ab:function(s){
        if(typeof ArrayBuffer !=='undefined'){
          let buf=new ArrayBuffer(s.length);
          let view=new Uint8Array(buf);
          for(var i=0;i!=s.length;++i){
            view[i]=s.charCodeAt(i) & 0xFF;
          }
          return buf;
        }else{
          let buf=new Array(s.length);
          for(var i=0; i!=s.length;++i){
            buf[i]=s.charCodeAt(i) & 0xFF;
            return buf;
          }
        }
      }
```

# 测试

运行测试

