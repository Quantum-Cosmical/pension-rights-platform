# pension-rights-platform
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>前科人员养老保险权益保障平台</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Microsoft YaHei', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        
        h1 {
            color: #2c3e50;
            font-size: 2.5em;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            color: #7f8c8d;
            font-size: 1.2em;
            margin-bottom: 20px;
        }
        
        .nav-tabs {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }
        
        .nav-tab {
            background: rgba(255, 255, 255, 0.9);
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 16px;
            font-weight: 500;
        }
        
        .nav-tab:hover {
            background: #667eea;
            color: white;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }
        
        .nav-tab.active {
            background: #667eea;
            color: white;
        }
        
        .content-area {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            padding: 30px;
            min-height: 600px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .card {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            border-radius: 12px;
            padding: 20px;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }
        
        .card h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.3em;
        }
        
        .card p {
            color: #555;
            line-height: 1.6;
        }
        
        .timeline {
            position: relative;
            padding: 20px 0;
        }
        
        .timeline-item {
            background: #f8f9fa;
            border-left: 4px solid #667eea;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 0 8px 8px 0;
            transition: all 0.3s ease;
        }
        
        .timeline-item:hover {
            background: #e8f4fd;
            transform: translateX(5px);
        }
        
        .timeline-year {
            font-weight: bold;
            color: #667eea;
            font-size: 1.1em;
        }
        
        .search-box {
            width: 100%;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            margin-bottom: 20px;
            transition: border-color 0.3s ease;
        }
        
        .search-box:focus {
            outline: none;
            border-color: #667eea;
        }
        
        .btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s ease;
            margin: 5px;
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }
        
        .stat-card {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 20px;
            border-radius: 12px;
            text-align: center;
        }
        
        .stat-number {
            font-size: 2em;
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 0.9em;
            opacity: 0.9;
        }
        
        .case-item {
            background: #f8f9fa;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 15px;
            border-left: 4px solid #28a745;
        }
        
        .case-title {
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .case-detail {
            color: #555;
            margin-bottom: 10px;
        }
        
        .case-tag {
            display: inline-block;
            background: #e9ecef;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 0.85em;
            margin-right: 5px;
            margin-bottom: 5px;
        }
        
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
        }
        
        .modal-content {
            background-color: white;
            margin: 5% auto;
            padding: 30px;
            border-radius: 15px;
            width: 80%;
            max-width: 600px;
            animation: slideIn 0.3s ease;
        }
        
        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }
        
        .close:hover {
            color: #000;
        }
        
        .progress-bar {
            width: 100%;
            height: 20px;
            background: #e9ecef;
            border-radius: 10px;
            overflow: hidden;
            margin: 10px 0;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(45deg, #667eea, #764ba2);
            transition: width 0.3s ease;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>前科人员养老保险权益保障平台</h1>
            <p class="subtitle">基于法治理念与社会公平的综合服务系统</p>
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number">1951</div>
                    <div class="stat-label">政策起始年份</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">31</div>
                    <div class="stat-label">省级行政区</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">3</div>
                    <div class="stat-label">核心规范逻辑</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">2024</div>
                    <div class="stat-label">最新研究年份</div>
                </div>
            </div>
        </header>

        <nav class="nav-tabs">
            <button class="nav-tab active" onclick="showTab('overview')">核心论点</button>
            <button class="nav-tab" onclick="showTab('policy')">政策法规</button>
            <button class="nav-tab" onclick="showTab('analysis')">现状分析</button>
            <button class="nav-tab" onclick="showTab('rights')">权益保护</button>
            <button class="nav-tab" onclick="showTab('cases')">案例研究</button>
            <button class="nav-tab" onclick="showTab('services')">服务工具</button>
        </nav>

        <main class="content-area">
            <!-- 核心论点标签页 -->
            <div id="overview" class="tab-content active">
                <h2>核心论点概述</h2>
                <p>在基本养老保险待遇认定事项上对前科人员进行区别对待的做法长期存在于我国养老保险制度实践中。[[1]]</p>
                
                <div class="card-grid">
                    <div class="card">
                        <h3>🔍 问题识别</h3>
                        <p>削减前科人员基本养老保险待遇的方式是不认定其服刑前的本企业工龄或工作年限，本质上是通过否定国家应当为前科人员承担养老保险缴费成本，剥夺其经济利益。[[2]]</p>
                    </div>
                    
                    <div class="card">
                        <h3>⚖️ 规范分析</h3>
                        <p>不承认前科人员养老保险国家缴费年限，削减其应享受的基本养老保险待遇，在手段适当性和规定必要性上存在明显缺陷。[[3]]</p>
                    </div>
                    
                    <div class="card">
                        <h3>🌍 实效影响</h3>
                        <p>在个人、社会、政治三个层面均会产生严重负面效应，包括加重经济负担、提高回归社会难度、不符合宽严相济政策等。[[4]]</p>
                    </div>
                    
                    <div class="card">
                        <h3>📋 三重逻辑</h3>
                        <p>权利义务相一致原则、按劳分配原则、实质平等理念，分别构成了认定前科人员基本养老保险待遇的生成逻辑、历史逻辑、分配逻辑。[[5]]</p>
                    </div>
                </div>

                <h3 style="margin-top: 30px;">政策演变时间线</h3>
                <div class="timeline">
                    <div class="timeline-item">
                        <div class="timeline-year">1951-1953年</div>
                        <p>《劳动保险条例》及实施细则首次规定养老待遇与本企业工龄关系，区分反革命犯罪与其他犯罪的工龄计算。[[6]]</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-year">1959年</div>
                        <p>《内务部复函》规定受过刑事处分原则上从重新参加工作之日起计算工作年限。[[7]]</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-year">1986-2005年</div>
                        <p>养老保险制度转型，建立"统账结合"模式，出现"视同缴费年限"概念。[[8]]</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-year">1995年</div>
                        <p>《劳动部复函》规定从实行个人缴费时间作为连续工龄起始时间，影响前科人员待遇。[[9]]</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-year">2024年</div>
                        <p>《劳动保险条例》废止，前科人员养老保险待遇认定问题面临规范空白。[[10]]</p>
                    </div>
                </div>
            </div>

            <!-- 政策法规标签页 -->
            <div id="policy" class="tab-content">
                <h2>政策法规中心</h2>
                <input type="text" class="search-box" placeholder="搜索法律法规、政策文件..." onkeyup="searchPolicies(this.value)">
                
                <h3>中央规范演变</h3>
                <div class="card-grid">
                    <div class="card">
                        <h3>📜 早期规范</h3>
                        <p>1953年《劳动保险条例实施细则修正草案》明确养老保险待遇与本企业工龄关系，对犯罪被剥夺政治权利者的工龄计算作出规定。[[11]]</p>
                        <button class="btn" onclick="showPolicyDetail('early')">查看详情</button>
                    </div>
                    
                    <div class="card">
                        <h3>🔄 转型期规范</h3>
                        <p>1995年《复函》指出从各地实行职工个人缴纳养老保险费的时间作为除名职工计算连续工龄的起始时间。[[12]]</p>
                        <button class="btn" onclick="showPolicyDetail('transition')">查看详情</button>
                    </div>
                    
                    <div class="card">
                        <h3>⚖️ 现行框架</h3>
                        <p>2010年《社会保险法》第13条规定视同缴费年限期间应当缴纳的基本养老保险费由政府承担。[[13]]</p>
                        <button class="btn" onclick="showPolicyDetail('current')">查看详情</button>
                    </div>
                </div>

                <h3 style="margin-top: 30px;">地方规范对比</h3>
                <div class="card-grid">
                    <div class="card">
                        <h3>✅ 支持承认地区</h3>
                        <p><strong>辽宁省：</strong>对职工在服刑或劳教之前的缴费年限（含视同缴费年限）予以承认。[[14]]</p>
                        <p><strong>福建省：</strong>保留公职者，其符合规定可视同的缴费年限可与实际缴费年限合并计算。[[15]]</p>
                    </div>
                    
                    <div class="card">
                        <h3>❌ 不支持承认地区</h3>
                        <p>江苏省、浙江省、陕西省、重庆市等省市仅承认实际缴费年限，不承认视同缴费年限。[[16]]</p>
                    </div>
                    
                    <div class="card">
                        <h3>🔄 附条件支持地区</h3>
                        <p><strong>山东省：</strong>个别因过失犯罪除外，其工龄均从刑满释放后重新参加工作之日起计算。[[17]]</p>
                    </div>
                </div>
            </div>

            <!-- 现状分析标签页 -->
            <div id="analysis" class="tab-content">
                <h2>现状深度分析</h2>
                
                <h3>规范分析：合比例性缺失</h3>
                <div class="card-grid">
                    <div class="card">
                        <h3>🎯 手段适当性不足</h3>
                        <p>关于受过刑事处罚会影响养老保险待遇这一问题的规定并不具有广泛的社会知晓度，难以实现提升威慑效果的目的。[[18]]</p>
                        <div class="progress-bar">
                            <div class="progress-fill" style="width: 25%;"></div>
                        </div>
                        <p>适当性评分：25%</p>
                    </div>
                    
                    <div class="card">
                        <h3>📏 规定必要性存疑</h3>
                        <p>部分地方政府采取"一刀切"认定模式，忽略了不同犯罪之间在主观恶性以及社会危害性上的差异。[[19]]</p>
                        <div class="progress-bar">
                            <div class="progress-fill" style="width: 35%;"></div>
                        </div>
                        <p>必要性评分：35%</p>
                    </div>
                </div>

                <h3 style="margin-top: 30px;">实效考察：三重负面效应</h3>
                <div class="card-grid">
                    <div class="card">
                        <h3>👤 个人层面</h3>
                        <p>加重了前科人员经济生活负担，不利于前科人员顺利回归家庭。[[20]]</p>
                        <ul style="margin-left: 20px; margin-top: 10px;">
                            <li>养老保险缴费成本完全由个人承担</li>
                            <li>年老时可能成为家庭负担</li>
                            <li>加剧家庭关系隔阂</li>
                        </ul>
                    </div>
                    
                    <div class="card">
                        <h3>🏘️ 社会层面</h3>
                        <p>提高了前科人员回归社会的难度，影响社会安定稳定。[[21]]</p>
                        <ul style="margin-left: 20px; margin-top: 10px;">
                            <li>过于严苛的犯罪附随后果是回归社会的主要障碍</li>
                            <li>可能提高再犯罪率</li>
                            <li>增加社会不安定因素</li>
                        </ul>
                    </div>
                    
                    <div class="card">
                        <h3>🏛️ 政治层面</h3>
                        <p>不符合宽严相济的基本刑事政策，过度苛责弱势群体犯罪人有损执政党权威。[[22]]</p>
                        <ul style="margin-left: 20px; margin-top: 10px;">
                            <li>违背"宽严相济"理念</li>
                            <li>对弱势群体缺乏关照</li>
                            <li>不符合以人民为中心思想</li>
                        </ul>
                    </div>
                </div>

                <h3 style="margin-top: 30px;">合法性分析</h3>
                <div class="card">
                    <h3>⚖️ 不同类规范合法性互斥</h3>
                    <p>国务院部委就这一问题作出的规定、回函和部分地方政府制定的规范性文件规定内容的合法性有待商榷。[[23]]</p>
                    <p>1959年《复函》、1995年《复函》直接扩大了不享有养老保险国家缴费年限待遇的对象群体，与《劳动保险条例实施细则修正草案》中的相关规定产生了直接冲突。[[24]]</p>
                </div>
            </div>

            <!-- 权益保护标签页 -->
            <div id="rights" class="tab-content">
                <h2>权益保护指南</h2>
                
                <div class="card-grid">
                    <div class="card">
                        <h3>🛡️ 前科人员权益</h3>
                        <p>基于权利义务相一致原则，劳动者因自身劳动贡献而享受养老保险国家缴费年限待遇，受过刑事处罚不会增减劳动者既有的劳动成果。[[25]]</p>
                        <button class="btn" onclick="showRightsGuide('individual')">个人维权指南</button>
                        <button class="btn" onclick="calculateBenefits()">待遇计算器</button>
                    </div>
                    
                    <div class="card">
                        <h3>🏢 政府职员指引</h3>
                        <p>在养老保险实施全国统筹的背景之下，重新构造全国统一的前科人员基本养老保险待遇认定方案具有紧迫性。[[26]]</p>
                        <button class="btn" onclick="showRightsGuide('government')">执行标准</button>
                        <button class="btn" onclick="showRightsGuide('coordination')">跨地区协调</button>
                    </div>
                    
                    <div class="card">
                        <h3>🔬 研究人员资源</h3>
                        <p>构造新认定方案的必要性遵循：权利义务相一致原则、按劳分配原则、实质平等理念。[[27]]</p>
                        <button class="btn" onclick="showRightsGuide('research')">研究工具</button>
                        <button class="btn" onclick="showRightsGuide('data')">数据共享</button>
                    </div>
                </div>

                <h3 style="margin-top: 30px;">三重规范逻辑详解</h3>
                <div class="timeline">
                    <div class="timeline-item">
                        <div class="timeline-year">生成逻辑</div>
                        <p><strong>权利义务相一致原则：</strong>国家承担公民的养老保险国家缴费年限构成了公民履行劳动义务的前提之一。[[28]]</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-year">历史逻辑</div>
                        <p><strong>按劳分配原则：</strong>国家在这一期间所承担的养老保险缴费成本，实际上是一种并未即时直接发放给劳动者本人的间接劳动报酬。[[29]]</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-year">分配逻辑</div>
                        <p><strong>实质平等理念：</strong>社会保障实际上是对收入和财富的二次分配，功能追求在于实现实质平等。[[30]]</p>
                    </div>
                </div>
            </div>

            <!-- 案例研究标签页 -->
            <div id="cases" class="tab-content">
                <h2>案例研究库</h2>
                <input type="text" class="search-box" placeholder="搜索案例..." onkeyup="searchCases(this.value)">
                
                <h3>司法实践分类</h3>
                <div class="case-item">
                    <div class="case-title">✅ 支持承认案例</div>
                    <div class="case-detail">
                        <p><strong>河北某地案件：</strong>人民法院明确支持前科人员连续工龄应当得到认定，并视作养老保险视同缴费年限，同时在说理部分指出1959年《复函》的规定与现行国家政策相悖。[[31]]</p>
                    </div>
                    <div class="case-tag">河北省</div>
                    <div class="case-tag">支持承认</div>
                    <div class="case-tag">否定旧规</div>
                    <button class="btn" onclick="showCaseDetail('hebei')">查看详情</button>
                </div>

                <div class="case-item">
                    <div class="case-title">🔄 变相承认案例</div>
                    <div class="case-detail">
                        <p><strong>河南某地案件：</strong>人民法院援引了当地关于不将前科人员连续工龄认定为养老保险视同缴费年限的规范性文件，但认为不承认养老保险视同缴费年限，并不与养老保险转制前职工连续工龄满10年即可按月享受养老保险待遇的规定相冲突。[[32]]</p>
                    </div>
                    <div class="case-tag">河南省</div>
                    <div class="case-tag">变相承认</div>
                    <div class="case-tag">灵活处理</div>
                    <button class="btn" onclick="showCaseDetail('henan')">查看详情</button>
                </div>

                <div class="case-item">
                    <div class="case-title">❌ 不支持承认案例</div>
                    <div class="case-detail">
                        <p><strong>江苏、山东案件：</strong>人民法院便以1959年《复函》作为依据，在援引地方政府作出的相应规定后，不支持承认前科人员养老保险视同缴费年限。[[33]]</p>
                    </div>
                    <div class="case-tag">江苏省</div>
                    <div class="case-tag">山东省</div>
                    <div class="case-tag">不支持承认</div>
                    <button class="btn" onclick="showCaseDetail('jiangsu')">查看详情</button>
                </div>

                <h3 style="margin-top: 30px;">案例统计分析</h3>
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-number">3</div>
                        <div class="stat-label">主要裁判类型</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">多省</div>
                        <div class="stat-label">地域差异明显</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">复杂</div>
                        <div class="stat-label">历史遗留问题</div>
                    </div>
                </div>
            </div>

            <!-- 服务工具标签页 -->
            <div id="services" class="tab-content">
                <h2>智能服务工具</h2>
                
                <div class="card-grid">
                    <div class="card">
                        <h3>🤖 智能咨询助手</h3>
                        <p>基于论文内容的自动问答系统，为您提供专业的政策解读和权益保护建议。</p>
                        <button class="btn" onclick="startChat()">开始咨询</button>
                    </div>
                    
                    <div class="card">
                        <h3>📊 政策影响评估</h3>
                        <p>模拟不同政策选择对个人养老金待遇的具体影响，帮助您做出明智决策。</p>
                        <button class="btn" onclick="startAssessment()">开始评估</button>
                    </div>
                    
                    <div class="card">
                        <h3>🗺️ 地区政策对比</h3>
                        <p>对比不同地区的养老保险政策差异，了解您所在地区的具体规定。</p>
                        <button class="btn" onclick="compareRegions()">开始对比</button>
                    </div>
                    
                    <div class="card">
                        <h3>📝 维权路径规划</h3>
                        <p>基于案例库分析，为您推荐最优的权益保护策略和法律途径。</p>
                        <button class="btn" onclick="planRightsProtection()">规划路径</button>
                    </div>
                    
                    <div class="card">
                        <h3>📚 学习资源中心</h3>
                        <p>提供相关法律法规、学术研究、政策解读等学习资料。</p>
                        <button class="btn" onclick="accessResources()">访问资源</button>
                    </div>
                    
                    <div class="card">
                        <h3>👥 专家咨询服务</h3>
                        <p>连接法律专家、政策研究者，提供一对一的专业咨询服务。</p>
                        <button class="btn" onclick="contactExpert()">联系专家</button>
                    </div>
                </div>

                <h3 style="margin-top: 30px;">快速工具入口</h3>
                <div style="display: flex; flex-wrap: wrap; gap: 10px;">
                    <button class="btn" onclick="quickTool('calculator')">养老金计算器</button>
                    <button class="btn" onclick="quickTool('eligibility')">资格自检</button>
                    <button class="btn" onclick="quickTool('document')">文书生成</button>
                    <button class="btn" onclick="quickTool('timeline')">维权时间线</button>
                    <button class="btn" onclick="quickTool('appeal')">申诉指南</button>
                    <button class="btn" onclick="quickTool('compensation')">补偿估算</button>
                </div>
            </div>
        </main>
    </div>

    <!-- 模态框 -->
    <div id="modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal()">&times;</span>
            <div id="modal-body"></div>
        </div>
    </div>

    <script>
        // 标签页切换功能
        function showTab(tabName) {
            // 隐藏所有标签页内容
            const tabContents = document.querySelectorAll('.tab-content');
            tabContents.forEach(tab => tab.classList.remove('active'));
            
            // 移除所有标签的active类
            const tabs = document.querySelectorAll('.nav-tab');
            tabs.forEach(tab => tab.classList.remove('active'));
            
            // 显示选中的标签页内容
            document.getElementById(tabName).classList.add('active');
            
            // 为选中的标签添加active类
            event.target.classList.add('active');
        }

        // 模态框功能
        function showModal(content) {
            document.getElementById('modal-body').innerHTML = content;
            document.getElementById('modal').style.display = 'block';
        }

        function closeModal() {
            document.getElementById('modal').style.display = 'none';
        }

        // 政策详情显示
        function showPolicyDetail(type) {
            let content = '';
            switch(type) {
                case 'early':
                    content = `
                        <h3>早期规范详情</h3>
                        <p>1953年《劳动保险条例实施细则修正草案》规定：</p>
                        <ul>
                            <li>因反革命罪行被剥夺政治权利者的本企业工龄需从恢复政治权利之日起重新计算</li>
                            <li>因其他犯罪行为而被剥夺政治权利者的本企业工龄可以与被剥夺政治权利前的工龄合并计算</li>
                        </ul>
                        <p>这表明犯有反革命罪行的劳动者犯罪前的本企业工龄不被认定。[[34]]</p>
                    `;
                    break;
                case 'transition':
                    content = `
                        <h3>转型期规范详情</h3>
                        <p>1995年《劳动部复函》规定：</p>
                        <ul>
                            <li>从各地实行职工个人缴纳养老保险费的时间作为除名职工计算连续工龄的起始时间</li>
                            <li>重新计算受过刑事处罚劳动者的连续工龄意味着相关劳动者将不享有视同缴费年限的待遇</li>
                        </ul>
                        <p>直接导致其能够获得的养老保险金减少，甚至会因缴费年限不足而无法享受养老保险。[[35]]</p>
                    `;
                    break;
                case 'current':
                    content = `
                        <h3>现行框架详情</h3>
                        <p>2010年《社会保险法》第13条规定：</p>
                        <blockquote>
                            "国有企业、事业单位职工参加基本养老保险前，视同缴费年限期间应当缴纳的基本养老保险费由政府承担。"
                        </blockquote>
                        <p>这为解决养老保险转制成本提供了法律依据。[[36]]</p>
                    `;
                    break;
            }
            showModal(content);
        }

        // 权益保护指南
        function showRightsGuide(type) {
            let content = '';
            switch(type) {
                case 'individual':
                    content = `
                        <h3>个人维权指南</h3>
                        <ol>
                            <li><strong>了解自身权益：</strong>查询当地养老保险政策，了解视同缴费年限认定标准</li>
                            <li><strong>收集证据材料：</strong>准备工作证明、缴费记录、刑事判决书等</li>
                            <li><strong>行政申诉：</strong>向当地社保部门提出申诉，要求重新认定缴费年限</li>
                            <li><strong>行政复议：</strong>对行政决定不服的，可申请行政复议</li>
                            <li><strong>司法诉讼：</strong>必要时可向人民法院提起行政诉讼</li>
                        </ol>
                        <p>基于权利义务相一致原则，您有权享受基于劳动贡献的养老保险待遇。[[37]]</p>
                    `;
                    break;
                case 'government':
                    content = `
                        <h3>政府职员执行标准</h3>
                        <ul>
                            <li><strong>统一认定标准：</strong>按照三重规范逻辑执行认定工作</li>
                            <li><strong>区分犯罪类型：</strong>考虑主观恶性和社会危害性差异</li>
                            <li><strong>保护弱势群体：</strong>特别关注国企改制等历史因素</li>
                            <li><strong>程序公正：</strong>确保认定过程透明、可申诉</li>
                        </ul>
                        <p>在养老保险实施全国统筹背景下，需要构造全国统一的认定方案。[[38]]</p>
                    `;
                    break;
                case 'research':
                    content = `
                        <h3>研究工具资源</h3>
                        <ul>
                            <li><strong>政策文本数据库：</strong>收录中央和地方相关政策文件</li>
                            <li><strong>司法案例库：</strong>整理相关裁判文书和判决理由</li>
                            <li><strong>统计分析工具：</strong>提供数据可视化和趋势分析</li>
                            <li><strong>国际比较研究：</strong>借鉴其他国家相关制度设计</li>
                        </ul>
                        <p>研究应遵循权利义务相一致、按劳分配、实质平等三重逻辑。[[39]]</p>
                    `;
                    break;
            }
            showModal(content);
        }

        // 案例详情显示
        function showCaseDetail(caseId) {
            let content = '';
            switch(caseId) {
                case 'hebei':
                    content = `
                        <h3>河北某地支持承认案例</h3>
                        <p><strong>案件背景：</strong>前科人员要求认定服刑前工龄为视同缴费年限</p>
                        <p><strong>裁判要点：</strong></p>
                        <ul>
                            <li>人民法院明确支持前科人员连续工龄应当得到认定</li>
                            <li>将连续工龄视作养老保险视同缴费年限</li>
                            <li>在说理部分指出1959年《复函》的规定与现行国家政策相悖</li>
                        </ul>
                        <p><strong>意义：</strong>体现了司法机关对不合理行政规范的积极审查态度。[[40]]</p>
                    `;
                    break;
                case 'henan':
                    content = `
                        <h3>河南某地变相承认案例</h3>
                        <p><strong>案件背景：</strong>前科人员要求享受养老保险待遇</p>
                        <p><strong>裁判要点：</strong></p>
                        <ul>
                            <li>援引当地不承认视同缴费年限的规范性文件</li>
                            <li>认为不承认视同缴费年限不与转制前规定冲突</li>
                            <li>以职工参加工作时间为准，支持享受养老保险待遇</li>
                        </ul>
                        <p><strong>意义：</strong>实际上是对前科人员连续工龄和养老保险视同缴费年限的变相承认。[[41]]</p>
                    `;
                    break;
                case 'jiangsu':
                    content = `
                        <h3>江苏、山东不支持承认案例</h3>
                        <p><strong>案件背景：</strong>前科人员要求认定视同缴费年限</p>
                        <p><strong>裁判要点：</strong></p>
                        <ul>
                            <li>以1959年《复函》作为裁判依据</li>
                            <li>援引地方政府相应规定</li>
                            <li>不支持承认前科人员养老保险视同缴费年限</li>
                        </ul>
                        <p><strong>意义：</strong>体现了严格遵循既有规范的传统司法态度。[[42]]</p>
                    `;
                    break;
            }
            showModal(content);
        }

        // 养老金计算器
        function calculateBenefits() {
            const content = `
                <h3>养老金待遇计算器</h3>
                <div style="margin: 20px 0;">
                    <label>工作年限（含视同缴费年限）：</label>
                    <input type="number" id="workYears" placeholder="请输入工作年限" style="width: 100%; padding: 8px; margin: 5px 0;">
                    
                    <label>实际缴费年限：</label>
                    <input type="number" id="actualYears" placeholder="请输入实际缴费年限" style="width: 100%; padding: 8px; margin: 5px 0;">
                    
                    <label>平均缴费工资指数：</label>
                    <input type="number" id="salaryIndex" placeholder="请输入缴费工资指数" step="0.1" style="width: 100%; padding: 8px; margin: 5px 0;">
                    
                    <label>当地平均工资：</label>
                    <input type="number" id="avgSalary" placeholder="请输入当地平均工资" style="width: 100%; padding: 8px; margin: 5px 0;">
                </div>
                <button class="btn" onclick="performCalculation()">计算养老金</button>
                <div id="calculationResult" style="margin-top: 20px;"></div>
            `;
            showModal(content);
        }

        function performCalculation() {
            const workYears = document.getElementById('workYears').value;
            const actualYears = document.getElementById('actualYears').value;
            const salaryIndex = document.getElementById('salaryIndex').value;
            const avgSalary = document.getElementById('avgSalary').value;
            
            if (!workYears || !actualYears || !salaryIndex || !avgSalary) {
                document.getElementById('calculationResult').innerHTML = '<p style="color: red;">请填写完整信息</p>';
                return;
            }
            
            // 简化的养老金计算公式（示例）
            const basicPension = avgSalary * (1 + salaryIndex) / 2 * workYears * 0.01;
            const personalPension = actualYears * salaryIndex * avgSalary * 0.01 / 195; // 假设个人账户储存额
            const totalPension = basicPension + personalPension;
            
            document.getElementById('calculationResult').innerHTML = `
                <div style="background: #f0f8ff; padding: 15px; border-radius: 8px;">
                    <h4>计算结果：</h4>
                    <p>基础养老金：${basicPension.toFixed(2)} 元/月</p>
                    <p>个人账户养老金：${personalPension.toFixed(2)} 元/月</p>
                    <p><strong>预计月养老金总额：${totalPension.toFixed(2)} 元</strong></p>
                    <p style="color: #666; font-size: 0.9em; margin-top: 10px;">
                        注：此为估算结果，实际金额以社保部门计算为准
                    </p>
                </div>
            `;
        }

        // 搜索功能
        function searchPolicies(keyword) {
            // 实际应用中这里会调用搜索API
            console.log('搜索政策：', keyword);
        }

        function searchCases(keyword) {
            // 实际应用中这里会调用搜索API
            console.log('搜索案例：', keyword);
        }

        // 快速工具功能
        function quickTool(toolType) {
            let content = '';
            switch(toolType) {
                case 'calculator':
                    calculateBenefits();
                    break;
                case 'eligibility':
                    content = `
                        <h3>资格自检工具</h3>
                        <div style="margin: 20px 0;">
                            <label>是否有前科记录？</label>
                            <select style="width: 100%; padding: 8px; margin: 5px 0;">
                                <option>请选择</option>
                                <option>是</option>
                                <option>否</option>
                            </select>
                            
                            <label>犯罪类型？</label>
                            <select style="width: 100%; padding: 8px; margin: 5px 0;">
                                <option>请选择</option>
                                <option>过失犯罪</option>
                                <option>故意犯罪</option>
                                <option>危害国家安全犯罪</option>
                            </select>
                            
                            <label>工作起始时间？</label>
                            <input type="date" style="width: 100%; padding: 8px; margin: 5px 0;">
                        </div>
                        <button class="btn">开始自检</button>
                    `;
                    showModal(content);
                    break;
                case 'document':
                    content = `
                        <h3>文书生成工具</h3>
                        <p>选择需要生成的文书类型：</p>
                        <div style="display: flex; flex-direction: column; gap: 10px; margin: 20px 0;">
                            <button class="btn">行政申诉书</button>
                            <button class="btn">行政复议申请书</button>
                            <button class="btn">行政诉讼起诉状</button>
                            <button class="btn">养老保险待遇申请表</button>
                        </div>
                    `;
                    showModal(content);
                    break;
                default:
                    content = `<h3>${toolType} 工具</h3><p>该功能正在开发中，敬请期待...</p>`;
                    showModal(content);
            }
        }

        // 其他功能函数
        function startChat() {
            showModal('<h3>智能咨询助手</h3><p>AI助手正在为您连接中...<br>您可以咨询关于前科人员养老保险的任何问题。</p>');
        }

        function startAssessment() {
            showModal('<h3>政策影响评估</h3><p>请输入您的具体情况，我们将为您评估不同政策选择的影响。</p>');
        }

        function compareRegions() {
            showModal('<h3>地区政策对比</h3><p>选择您要对比的地区，查看政策差异。</p>');
        }

        function planRightsProtection() {
            showModal('<h3>维权路径规划</h3><p>基于您的情况，我们将为您推荐最优的维权策略。</p>');
        }

        function accessResources() {
            showModal('<h3>学习资源中心</h3><p>提供丰富的学习资料和专业文献。</p>');
        }

        function contactExpert() {
            showModal('<h3>专家咨询服务</h3><p>连接专业律师和政策研究者，获得一对一指导。</p>');
        }

        // 页面加载完成后的初始化
        document.addEventListener('DOMContentLoaded', function() {
            // 添加平滑滚动效果
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                });
            });

            // 点击模态框外部关闭
            window.onclick = function(event) {
                const modal = document.getElementById('modal');
                if (event.target == modal) {
                    modal.style.display = 'none';
                }
            }
        });
    </script>
</body>
</html>
