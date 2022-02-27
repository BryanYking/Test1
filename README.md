# Test1构造网格数据结构的函数
function createNet(begin, diff) {   // begin,diff是参数，begin是初始价格，diff是网格间距（等差网格的间距是价格）
    var oneSideNums = 10            // 网格向上、向下一边生成10条线，上图是一边生成2条（AB一边,CD一边），生成10条的自行脑补画面
    var up = []                     // 用来储存向上的“网格线”数据结构
    var down = []                   // 用来储存向下的“网格线”数据结构
    for (var i = 0 ; i < oneSideNums ; i++) {    // 根据oneSideNums的大小确定次数，循环构造“网格线”数据结构
        var upObj = {                            // 构造一条向上的“网格线”数据结构
            buy : false,                         // 买入标记，初始标记为false ，意思为没有买入
            sell : false,                        // 卖出标记....
            price : begin + diff / 2 + i * diff, // 这条“网格线”表示的价格位，可以观察根据循环进行，价格位是依次升高的
        }
        up.push(upObj)                           // 构造好的“网格线”数据结构放入up数组

        var j = (oneSideNums - 1) - i            // 循环时 j 的变动是：9 ~ 0
        var downObj = {
            buy : false,
            sell : false,
            price : begin - diff / 2 - j * diff,
        }
        if (downObj.price <= 0) {                // 价格不能小于等于0 
            continue
        }
        down.push(downObj)                       // 构造好的“网格线”数据结构放入down
    }    

    return down.concat(up)                       // 把up加在down之后，形成一个网格线价格从小到大的网格数组结构
