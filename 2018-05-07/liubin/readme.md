![](aa.PNG)

js代码块
```
<script type="text/javascript">          
        //初始化echarts实例  
        var myChart = echarts.init(document.getElementById('chartmain'));          
        myChart.showLoading({  
            text: '正在努力的读取数据中...',    //loading  
        });  
        //异步加载的配置项和数据显示图表  
        function Data(){  
            $.ajax({
            	async: true, 
					type: "get",
					url: "http://api.shenjian.io/",
					data: {
						appid: "dd648129b0e17057b8901c27f4a88021"
					},
					dataType: "jsonp",
					success: function(text) {  
						//alert(text.data[0].MovieName);
						var A = [];
				        var B = [];
						for(var x = 0; x < text.data.length; x++) {
					A.push(text.data[x].MovieName);//将MoveNaneme存入xA
					B.push(text.data[x].BoxOffice);
					{
					}
                        	myChart.setOption({        
                            tooltip: {  
                                show: true  
                            },  
                            legend: {  
                                data:['金额/万元']  
                            },  
              
					xAxis: {
						
						data: A,
						axisLabel: {
							interval: 0,
							rotate: -25
							
						}
					},
                           yAxis: {},
                       	series: [{
					
						name: '金额/万元',
						type: 'bar',
						data: B,
					}]
                        })  
                        	myChart.hideLoading();  //loading hidden  
                    	}  
            }  
            })  
        }  
        Data();  
    </script>   


```
