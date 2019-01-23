# js_dynamic_add
js控制动态添加

```html
<div class="layui-form-item" id="saltIpGroup">
        <label class="layui-form-label">
            规格配置:
        </label>
        <div class="layui-input-block">
                {present name="goodslist['allnorm']"}
                
                {volist name="goodslist['allnorm']" id="va" key="k"}
                    <div class="input-group saltIp" style="width:100%;padding:0 0 1px 0;">
                        <input type="text" class="layui-input" id="saltIp" name="guige{$k}" style="max-width:145px;float: left;" placeholder="请输入规格" value="{$va[0]|default=''}" > 
                        <input type="text" class="layui-input" id="apiPort" name="jine{$k}" style="max-width:145px;float: left;" placeholder="请输入金额" value="{$va[1]|default=''}" >                     
                        <span class="input-group-btn">
                            <button  class="layui-btn" type="button" data-toggle="tooltip" title="删除" id="delSaltIpGrp" >-</button>
                        </span>
                    </div>
                {/volist}

                {/present}

            <button type="button" data-toggle="tooltip" title="新增" id="addSaltIpGrpBtn" onclick="addSaltIpGrp(this)" class="layui-btn">+</button>
        </div>
</div>
```

```js
<script>
    
    var index=parseInt("{$length|default=0}");
    document.getElementById("idx").value=index;
    function addSaltIpGrp(obj){ 
       index=index+1;
        html = '<div class="input-group saltIp" style="width:100%;padding:0 0 1px 0;">'+  
                    // '<label class="input-group-addon">IP:</label>'+  
                    '<input type="text" class="layui-input" id="saltIp" name="guige'+index+'" style="max-width:145px;float: left;" placeholder="请输入规格">'+  
                    // '<label class="input-group-addon">API端口:</label>'+  
                    '<input type="text" class="layui-input" id="apiPort" name="jine'+index+'" style="max-width:145px;float: left;" placeholder="请输入金额">'+                            
                    '<span class="input-group-btn">'+  
                        '<button  class="layui-btn" type="button" data-toggle="tooltip" title="删除" id="delSaltIpGrp" >-</button>'+
                    '</span>'+  
                '</div>'  
        obj.insertAdjacentHTML('beforebegin',html);
        document.getElementById("idx").value=index;
    }

    //减号
    $(document).on('click','#delSaltIpGrp',function(){  
    var el = this.parentNode.parentNode  
    var saltIp = $(this).parent().parent().find('#saltIp').val()  
    // if (saltIp == ""){  
        el.parentNode.removeChild(el)  
        return  
    // }  
    // alertify.confirm('您确定要删除选中的命令？',  
    // function(e){  
    //     if(e){  
    //         $.ajax({  
    //             'url':'/url',  
    //             'type':'POST',  
    //             'async':false,  
    //             'dataType':'json',  
    //             'data':{'type':'delSaltIp','projectId':projectId,'saltIp':saltIp},  
    //             'success':function(result){  
    //                 if (result.code){  
    //                     el.parentNode.removeChild(el)  
    //                 }else {  
    //                     showError(result.msg)  
    //                 }  
    //             }  
    //         })  
      
    //     }  
    // })  
      
})  
</script>
```