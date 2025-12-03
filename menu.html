import React, { useState, useEffect, useCallback, useMemo } from 'react';

// Firebase imports
import { initializeApp } from 'firebase/app';
import { getAuth, signInAnonymously, onAuthStateChanged } from 'firebase/auth';
import { getFirestore, doc, addDoc, onSnapshot, collection, deleteDoc, updateDoc, setLogLevel } from 'firebase/firestore';

// =================================================================
// 核心 Firebase 配置 (Core Firebase Configuration)
// =================================================================
const CUSTOM_FIREBASE_CONFIG = {
    apiKey: "AIzaSyB3o6MKpxCz1HvgR2k8wpDF9GDtMtZD3dc",
    authDomain: "junjunmenu.firebaseapp.com",
    projectId: "junjunmenu",
    storageBucket: "junjunmenu.firebasestorage.app",
    messagingSenderId: "107344539892",
    appId: "1:107344539892:web:92fa634f2a2bd0710e2ea1"
};

const appId = CUSTOM_FIREBASE_CONFIG.projectId || 'shared-menu-app';
const SHARED_COLLECTION_NAME = 'shared_menu_items';

let dbInstance = null;
let authInstance = null;

/**
 * 获取公共菜单集合的引用路径
 */
const getCollectionPath = () => `public/${appId}/${SHARED_COLLECTION_NAME}`;


// =================================================================
// 辅助图标组件 (Icons)
// 使用 SVG 定义以确保风格一致性
// =================================================================
const Home = ({ className = 'w-5 h-5' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>);
const ListChecks = ({ className = 'w-5 h-5' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M13 19h6"/><path d="M13 15h6"/><path d="M13 11h6"/><path d="M3 12l5-5 5 5"/><path d="M3 16h6"/></svg>);
const PlusCircle = ({ className = 'w-5 h-5' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><circle cx="12" cy="12" r="10"/><path d="M12 8v8"/><path d="M8 12h8"/></svg>);
const Trash2 = ({ className = 'w-5 h-5' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M3 6h18"/><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"/><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"/><line x1="10" x2="10" y1="11" y2="17"/><line x1="14" x2="14" y1="11" y2="17"/></svg>);
const Edit = ({ className = 'w-5 h-5' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M17 3a2.85 2.85 0 1 1 4 4L7.5 20.5 2 22l1.5-5.5Z"/></svg>);
const Check = ({ className = 'w-5 h-5' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M20 6 9 17l-5-5"/></svg>);
const X = ({ className = 'w-5 h-5' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M18 6 6 18"/><path d="m6 6 12 12"/></svg>);
const DishIcon = ({ className = 'w-6 h-6' }) => (<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M12 2a3 3 0 0 0-3 3v7a3 3 0 0 0 6 0V5a3 3 0 0 0-3-3Z"/><path d="M9 13.5v.5c0 4.3 3 7.6 6.8 8.1l.2.1h.5a8.496 8.496 0 0 0 3.7-2.9L22 17"/><path d="M15 13.5v.5c0 4.3-3 7.6-6.8 8.1l-.2.1h-.5c-3 0-5.6-1.5-7.3-4.1l-1.3-2"/><path d="M3 3h20"/></svg>);


// =================================================================
// 视图组件 (View Components)
// =================================================================

/**
 * 菜单添加页面 (Add View)
 */
const AddView = ({ db, userId, onSaveMessage }) => {
    const [dishName, setDishName] = useState('');
    const [dishCategory, setDishCategory] = useState('');
    const [isLoading, setIsLoading] = useState(false);

    const saveDish = async () => {
        if (!dishName.trim()) {
            onSaveMessage('菜名不能为空！', 'error');
            return;
        }

        setIsLoading(true);
        const category = dishCategory.trim().toLowerCase() || '其他';
        
        const newDish = {
            name: dishName.trim(),
            category: category, 
            createdAt: new Date().toISOString(),
            addedBy: userId 
        };

        try {
            const menuColRef = collection(db, getCollectionPath());
            await addDoc(menuColRef, newDish);
            onSaveMessage(`${dishName.trim()} 保存成功并已共享！`, 'success');
            setDishName('');
            setDishCategory('');
        } catch (error) {
            console.error("保存菜肴失败:", error);
            onSaveMessage(`保存失败: ${error.message}`, 'error');
        } finally {
            setIsLoading(false);
        }
    }

    return (
        <div className="space-y-8 p-6 bg-white rounded-2xl shadow-xl border border-[#D9C4A8]">
            <h2 className="text-2xl font-bold text-[#8B4513] border-b pb-3">✍️ 录入新菜谱</h2>
            <p className="text-gray-600">将您的新菜品加入共享菜单库，方便日后点餐和管理。</p>

            <div className="space-y-5">
                <input
                    type="text"
                    value={dishName}
                    onChange={(e) => setDishName(e.target.value)}
                    placeholder="菜名 (例: 红烧肉)"
                    className="w-full p-4 border border-[#B33939]/30 rounded-xl focus:ring-[#B33939] focus:border-[#B33939] transition duration-200 text-base shadow-sm"
                />
                <input
                    type="text"
                    value={dishCategory}
                    onChange={(e) => setDishCategory(e.target.value)}
                    placeholder="分类 (例: 沪菜, 荤菜, 节日)"
                    className="w-full p-4 border border-[#B33939]/30 rounded-xl focus:ring-[#B33939] focus:border-[#B33939] transition duration-200 text-base shadow-sm"
                />
                <button
                    onClick={saveDish}
                    disabled={isLoading}
                    className={`w-full text-white font-extrabold tracking-wider py-4 rounded-xl shadow-lg transition duration-200 transform hover:scale-[1.01] flex items-center justify-center ${
                        isLoading ? 'bg-[#B33939]/70 cursor-not-allowed' : 'bg-[#B33939] hover:bg-[#992D2D] active:bg-[#6F1A07]'
                    }`}
                >
                    {isLoading ? (
                        <>
                            <div className="animate-spin w-5 h-5 border-2 border-white border-t-transparent rounded-full mr-2"></div>
                            正在保存...
                        </>
                    ) : (
                        <>
                            <PlusCircle className="w-5 h-5 mr-2" />
                            保存新菜品
                        </>
                    )}
                </button>
            </div>
        </div>
    );
};

/**
 * 菜单列表与管理页面 (Manage View)
 */
const ManageView = ({ db, menuItems, onSaveMessage }) => {
    const [currentFilter, setCurrentFilter] = useState('All');
    const [editingId, setEditingId] = useState(null);
    const [editName, setEditName] = useState('');
    const [editCategory, setEditCategory] = useState('');

    // 提取所有分类并格式化
    const allCategories = useMemo(() => {
        const categories = new Set(menuItems.map(item => item.category));
        return ['All', ...Array.from(categories)].map(c => c.charAt(0).toUpperCase() + c.slice(1));
    }, [menuItems]);

    // 筛选菜单项
    const filteredItems = useMemo(() => {
        if (currentFilter === 'All') return menuItems;
        return menuItems.filter(item => item.category.toUpperCase() === currentFilter.toUpperCase());
    }, [menuItems, currentFilter]);

    // 删除菜肴
    const deleteDish = async (dishId, dishName) => {
        if (!confirm(`确定要永久删除菜单项 "${dishName}" 吗？该操作将从共享列表中移除。`)) return;

        try {
            const docRef = doc(db, getCollectionPath(), dishId);
            await deleteDoc(docRef);
            onSaveMessage(`${dishName} 已从共享列表中永久删除。`, 'success');
        } catch (error) {
            console.error("删除菜单项失败:", error);
            onSaveMessage('删除失败，请检查网络或权限。', 'error');
        }
    };
    
    // 启用编辑模式
    const startEdit = (item) => {
        setEditingId(item.id);
        setEditName(item.name);
        setEditCategory(item.category);
    };

    // 保存编辑
    const updateDish = async (dishId) => {
        if (!editName.trim()) {
            onSaveMessage('菜名不能为空！', 'error');
            return;
        }

        const newCategory = editCategory.trim().toLowerCase() || '其他';
        
        try {
            const docRef = doc(db, getCollectionPath(), dishId);
            await updateDoc(docRef, {
                name: editName.trim(),
                category: newCategory
            });

            onSaveMessage(`${editName.trim()} 已成功更新并共享！`, 'success');
            setEditingId(null); // 退出编辑模式
        } catch (error) {
            console.error("更新菜肴失败:", error);
            onSaveMessage(`更新失败: ${error.message}`, 'error');
        }
    };
    
    // 菜单列表渲染项
    const renderMenuItem = (item) => {
        const isEditing = editingId === item.id;
        const categoryDisplay = item.category.charAt(0).toUpperCase() + item.category.slice(1);
        
        return (
            <div key={item.id} className="flex justify-between items-center bg-white p-4 rounded-xl border border-gray-200 shadow-lg transition duration-150 hover:shadow-xl hover:bg-[#FFFDFB]">
                
                {isEditing ? (
                    // 编辑模式
                    <div className="flex-grow space-y-2">
                        <input
                            type="text"
                            value={editName}
                            onChange={(e) => setEditName(e.target.value)}
                            className="w-full p-2 text-base font-semibold border border-[#B33939] rounded-lg focus:ring-[#B33939] focus:border-[#B33939]"
                            placeholder="菜名"
                        />
                        <input
                            type="text"
                            value={editCategory}
                            onChange={(e) => setEditCategory(e.target.value)}
                            className="w-full p-2 text-sm border border-[#B33939]/50 rounded-lg focus:ring-[#B33939] focus:border-[#B33939]"
                            placeholder="分类"
                        />
                    </div>
                ) : (
                    // 显示模式
                    <div className="flex-grow flex items-center justify-start min-w-0 space-x-3">
                        <DishIcon className="w-6 h-6 text-[#B33939] flex-shrink-0" />
                        <div className="min-w-0">
                            <span className="text-gray-900 font-bold text-lg truncate block">{item.name}</span>
                            <span className="mt-1 flex-shrink-0 inline-block text-xs font-medium bg-[#8B4513]/10 text-[#8B4513] px-3 py-0.5 rounded-full shadow-inner">{categoryDisplay}</span>
                        </div>
                    </div>
                )}

                {/* 操作按钮 */}
                <div className="flex space-x-2 ml-4 flex-shrink-0">
                    {isEditing ? (
                        <>
                            {/* 保存/取消按钮 */}
                            <button onClick={() => updateDish(item.id)} className="text-green-600 hover:text-green-800 p-2 rounded-full hover:bg-green-100 transition duration-150 shadow-md" title="保存更改">
                                <Check />
                            </button>
                            <button onClick={() => setEditingId(null)} className="text-gray-500 hover:text-gray-700 p-2 rounded-full hover:bg-gray-100 transition duration-150 shadow-md" title="取消编辑">
                                <X />
                            </button>
                        </>
                    ) : (
                        <>
                            {/* 编辑/删除按钮 */}
                            <button onClick={() => startEdit(item)} className="text-blue-500 hover:text-blue-700 p-2 rounded-full hover:bg-blue-100 transition duration-150 shadow-sm" title="编辑菜肴">
                                <Edit />
                            </button>
                            <button onClick={() => deleteDish(item.id, item.name)} className="text-red-500 hover:text-red-700 p-2 rounded-full hover:bg-red-100 transition duration-150 shadow-sm" title="删除菜肴">
                                <Trash2 />
                            </button>
                        </>
                    )}
                </div>
            </div>
        );
    };


    return (
        <div className="space-y-6 p-6 bg-white rounded-2xl shadow-xl border border-[#D9C4A8]">
            <h2 className="text-2xl font-bold text-[#8B4513]">📋 菜单库总览 (共 {menuItems.length} 项)</h2>

            {/* 分类标签和过滤 */}
            <div className="flex flex-wrap gap-2 pt-2 pb-4 border-b border-[#D9C4A8] custom-scrollbar overflow-x-auto">
                {allCategories.map(category => (
                    <button
                        key={category}
                        onClick={() => setCurrentFilter(category)}
                        className={`px-4 py-1.5 text-sm font-semibold rounded-full transition duration-200 whitespace-nowrap shadow-md ${
                            category === currentFilter
                            ? 'bg-[#B33939] text-white hover:bg-[#992D2D] ring-2 ring-[#B33939]/50' 
                            : 'bg-[#FAF6F2] text-gray-700 hover:bg-[#F0EAE4] border border-[#D9C4A8]'
                        }`}
                    >
                        {category} ({category === 'All' 
                            ? menuItems.length 
                            : menuItems.filter(item => item.category.toUpperCase() === category.toUpperCase()).length
                        })
                    </button>
                ))}
            </div>

            {/* 菜单列表 */}
            <div className="space-y-4 max-h-[60vh] overflow-y-auto custom-scrollbar">
                {filteredItems.length === 0 ? (
                    <p className="text-gray-400 text-center py-10">
                        {menuItems.length === 0 ? "请先添加菜肴到菜单库！" : `在分类 "${currentFilter}" 下没有找到菜单。`}
                    </p>
                ) : (
                    filteredItems.map(renderMenuItem)
                )}
            </div>
        </div>
    );
};

/**
 * 随机点餐与推荐页面 (Recommend View)
 */
const RecommendView = ({ menuItems, onSaveMessage }) => {
    const [query, setQuery] = useState('');
    const [recommendation, setRecommendation] = useState(null);
    const [isLoading, setIsLoading] = useState(false);

    // 简单本地匹配逻辑（基于关键词匹配分类）
    const simpleLocalCategoryMatch = useCallback((query, items) => {
        const allCategories = [...new Set(items.map(item => item.category))];
        const lowerQuery = query.toLowerCase();
        
        const keywordMap = {
            '辣': '川菜', '清淡': '素食', '快': '快餐', '简单': '快餐',
            '汤': '汤', '粥': '粥', '早': '早餐', '家常': '家常菜',
            '饭': '主食', '肉': '荤菜', '鱼': '海鲜'
        };
        
        for (const category of allCategories) { if (lowerQuery.includes(category)) return category; }
        for (const keyword in keywordMap) {
            if (lowerQuery.includes(keyword)) {
                const matchedCategory = keywordMap[keyword].toLowerCase();
                if (allCategories.includes(matchedCategory)) return matchedCategory;
            }
        }
        
        return null;
    }, []);

    const handleRecommendation = async () => {
        if (menuItems.length === 0) {
            onSaveMessage('请先添加菜单，我才能帮你推荐哦！', 'error');
            return;
        }

        setIsLoading(true);
        setRecommendation(null);
        
        const matchedCategory = simpleLocalCategoryMatch(query, menuItems);
        
        let filteredDishes = menuItems;
        let recommendationSource = '从所有菜品中随机挑选';

        if (matchedCategory) {
            filteredDishes = menuItems.filter(item => item.category === matchedCategory);
            recommendationSource = `已匹配到分类: ${matchedCategory.charAt(0).toUpperCase() + matchedCategory.slice(1)}`;
        } else if (query.trim()) {
            recommendationSource = '未匹配到特定分类，随机挑选';
        }

        if (filteredDishes.length === 0) {
            filteredDishes = menuItems;
            recommendationSource = '匹配分类无菜，从所有菜品中随机挑选';
        }
        
        const randomIndex = Math.floor(Math.random() * filteredDishes.length);
        const dish = filteredDishes[randomIndex];

        await new Promise(resolve => setTimeout(resolve, 800)); // 模拟思考时间

        setRecommendation({
            name: dish.name,
            category: dish.category.charAt(0).toUpperCase() + dish.category.slice(1),
            source: recommendationSource
        });
        setIsLoading(false);
    };

    return (
        <div className="space-y-8 p-6 bg-white rounded-2xl shadow-xl border border-[#D9C4A8]">
            <h2 className="text-2xl font-bold text-[#8B4513] border-b pb-3">🍽️ 智能点餐机</h2>
            <p className="text-gray-600">输入您的要求，或直接点击按钮，让系统在共享菜单中随机为您挑选今日菜品。</p>

            <div className="space-y-5">
                <input
                    type="text"
                    value={query}
                    onChange={(e) => setQuery(e.target.value)}
                    placeholder="我想吃点清淡的... / 随便来个家常菜"
                    className="w-full p-4 border border-[#8B4513]/30 rounded-xl focus:ring-[#8B4513] focus:border-[#8B4513] transition duration-200 text-base shadow-sm"
                />
                <button
                    onClick={handleRecommendation}
                    disabled={isLoading || menuItems.length === 0}
                    className={`w-full text-white font-extrabold tracking-wider py-4 rounded-xl shadow-lg transition duration-200 transform hover:scale-[1.01] flex items-center justify-center ${
                        isLoading || menuItems.length === 0 ? 'bg-[#8B4513]/70 cursor-not-allowed' : 'bg-[#8B4513] hover:bg-[#6F3624] active:bg-[#4A2C2A]'
                    }`}
                >
                    {isLoading ? (
                        <>
                            <div className="animate-spin w-5 h-5 border-2 border-white border-t-transparent rounded-full mr-2"></div>
                            正在挑选...
                        </>
                    ) : (
                        <>
                            <Home className="w-5 h-5 mr-2" />
                            随机抽一个菜！
                        </>
                    )}
                </button>
            </div>

            {/* 推荐结果展示 - 使用高级卡片样式 */}
            <div className="min-h-[8rem] flex flex-col justify-center items-center text-center p-6 bg-[#FAF6F2] border border-[#D9C4A8] rounded-2xl shadow-inner">
                {recommendation ? (
                    <>
                        <p className="text-4xl font-extrabold text-[#B33939] mb-2 animate-bounce">{recommendation.name}！</p>
                        <p className="text-base text-gray-700">
                            所属分类：<span className="font-semibold text-[#8B4513]">{recommendation.category}</span>
                        </p>
                        <p className="text-xs text-gray-500 mt-1">({recommendation.source})</p>
                    </>
                ) : (
                    <p className="text-lg text-[#8B4513] font-medium">请点击按钮开始点餐！</p>
                )}
            </div>
        </div>
    );
};


// =================================================================
// 主应用组件 (Main App Component)
// =================================================================
const App = () => {
    const [currentView, setCurrentView] = useState('recommend'); 
    const [userId, setUserId] = useState(null);
    const [isFirebaseReady, setIsFirebaseReady] = useState(false);
    const [menuItems, setMenuItems] = useState([]);
    const [saveMessage, setSaveMessage] = useState({ text: '', type: 'info' });

    // 消息提示处理函数
    const handleSaveMessage = (text, type = 'info') => {
        setSaveMessage({ text, type });
        setTimeout(() => setSaveMessage({ text: '', type: 'info' }), 3000);
    };

    // Firebase 初始化与数据监听
    useEffect(() => {
        if (!CUSTOM_FIREBASE_CONFIG.apiKey) return;
        
        setLogLevel('debug'); 
        const app = initializeApp(CUSTOM_FIREBASE_CONFIG);
        dbInstance = getFirestore(app);
        authInstance = getAuth(app);
        
        const unsubscribeAuth = onAuthStateChanged(authInstance, async (user) => {
            if (user) {
                setUserId(user.uid);
                setIsFirebaseReady(true);
            } else {
                try {
                    await signInAnonymously(authInstance);
                } catch (error) {
                    console.error("Firebase 匿名登录失败:", error);
                    handleSaveMessage("认证失败，请检查 Firebase 匿名登录是否已启用。", 'error');
                }
            }
        });

        return () => unsubscribeAuth();
    }, []);

    // Firestore 数据监听
    useEffect(() => {
        if (!isFirebaseReady || !dbInstance) return;

        const menuColRef = collection(dbInstance, getCollectionPath());
        
        const unsubscribeSnapshot = onSnapshot(menuColRef, (snapshot) => {
            const fetchedItems = [];
            snapshot.forEach(doc => {
                fetchedItems.push({ id: doc.id, ...doc.data() });
            });
            setMenuItems(fetchedItems);
        }, (error) => {
            console.error("监听菜单数据失败:", error);
            handleSaveMessage('实时连接失败，请刷新重试。', 'error');
        });

        return () => unsubscribeSnapshot();
    }, [isFirebaseReady]);

    // 渲染当前视图
    const renderView = () => {
        if (!isFirebaseReady) {
            return (
                <div className="text-center py-20 bg-white rounded-2xl shadow-xl border border-[#D9C4A8]">
                    <div className="animate-spin inline-block w-10 h-10 border-4 border-[#B33939] border-t-transparent rounded-full"></div>
                    <p className="mt-4 text-[#B33939] font-semibold">正在连接您的私人菜单云端...</p>
                </div>
            );
        }

        switch (currentView) {
            case 'recommend':
                return <RecommendView menuItems={menuItems} onSaveMessage={handleSaveMessage} />;
            case 'manage':
                return <ManageView db={dbInstance} menuItems={menuItems} onSaveMessage={handleSaveMessage} />;
            case 'add':
                return <AddView db={dbInstance} userId={userId} onSaveMessage={handleSaveMessage} />;
            default:
                return <RecommendView menuItems={menuItems} onSaveMessage={handleSaveMessage} />;
        }
    };

    // 状态横幅样式
    const messageStyle = {
        success: 'bg-green-100 text-green-700 border-l-4 border-green-500',
        error: 'bg-red-100 text-red-700 border-l-4 border-red-500',
        info: 'bg-blue-100 text-blue-700 border-l-4 border-blue-500'
    };

    return (
        <div className="min-h-screen bg-[#FAF6F2] p-4 sm:p-8 flex flex-col items-center">
            <style jsx="true">{`
                /* Custom Scrollbar for better aesthetics */
                .custom-scrollbar::-webkit-scrollbar {
                    width: 6px;
                }
                .custom-scrollbar::-webkit-scrollbar-thumb {
                    background-color: #D9C4A8;
                    border-radius: 3px;
                }
                .custom-scrollbar::-webkit-scrollbar-track {
                    background-color: #F0EAE4;
                }
            `}</style>
            
            <div className="w-full max-w-2xl bg-[#FFFDFB] shadow-2xl rounded-3xl p-6 sm:p-8 lg:p-10 mb-6 border border-[#EBE3D7]">
                <h1 className="text-4xl font-extrabold text-[#B33939] mb-1 tracking-wide">
                    俊俊菜单菌
                    <DishIcon className="w-8 h-8 inline-block ml-3 transform translate-y-[-2px]" />
                </h1>
                <p className="text-sm text-gray-500 mb-4 border-b pb-4">
                    共享ID (用于验证连接): 
                    <span className="font-mono text-xs bg-[#FAF6F2] px-2 py-0.5 rounded ml-2 text-gray-600">
                        {userId ? `ID: ${userId.substring(0, 8)}... | 菜品总数: ${menuItems.length}` : '连接中...'}
                    </span>
                </p>

                {/* 消息提示区 */}
                {saveMessage.text && (
                    <div className={`p-3 mb-4 rounded-lg text-sm font-medium shadow-md ${messageStyle[saveMessage.type] || messageStyle.info}`}>
                        {saveMessage.text}
                    </div>
                )}
                
                {/* 优雅导航栏 */}
                <div className="flex justify-between p-1 bg-[#F0EAE4] rounded-xl shadow-inner mb-8">
                    {[
                        { key: 'recommend', label: '今天吃啥', icon: Home },
                        { key: 'manage', label: '管理菜单', icon: ListChecks },
                        { key: 'add', label: '添加菜品', icon: PlusCircle },
                    ].map(({ key, label, icon: Icon }) => (
                        <button
                            key={key}
                            onClick={() => setCurrentView(key)}
                            className={`flex-1 flex items-center justify-center py-2 sm:py-3 rounded-xl text-sm font-bold tracking-wider transition duration-300 ${
                                currentView === key 
                                    ? 'bg-[#8B4513] text-white shadow-lg shadow-[#8B4513]/30' 
                                    : 'text-gray-700 hover:bg-[#D9C4A8] hover:text-white'
                            }`}
                        >
                            <Icon className="w-5 h-5 mr-1.5" />
                            <span className="hidden sm:inline">{label}</span>
                        </button>
                    ))}
                </div>

                {/* 动态内容区域 */}
                {renderView()}
            </div>
            
        </div>
    );
};

export default App;

