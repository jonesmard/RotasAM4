import React, { useState, useMemo, useRef, useEffect } from 'react';
import { initializeApp } from 'firebase/app';
import { 
  getAuth, 
  signInAnonymously, 
  signInWithCustomToken, 
  onAuthStateChanged 
} from 'firebase/auth';
import { 
  getFirestore, 
  doc, 
  setDoc, 
  getDoc, 
  onSnapshot, 
  collection, 
  query, 
  deleteDoc,
  writeBatch
} from 'firebase/firestore';
import { 
  Plane, 
  MapPin, 
  DollarSign, 
  Search, 
  Map as MapIcon,
  Navigation,
  ArrowRight,
  CheckCircle2,
  Clock,
  TrendingUp,
  ChevronDown,
  Upload,
  Filter,
  Trash2,
  ChevronLeft,
  ChevronRight,
  User,
  Database,
  Loader2
} from 'lucide-react';

// --- CONFIGURAÇÃO FIREBASE ---
const firebaseConfig = JSON.parse(__firebase_config);
const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);
const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';

// --- AUXILIARES ---
const formatTime = (hours) => {
  if (isNaN(hours)) return "0h 0m";
  const h = Math.floor(hours);
  const m = Math.round((hours - h) * 60);
  return `${h}h ${m}m`;
};

const RouteCard = ({ data, isInUse, onToggleUse }) => {
  return (
    <div className={`relative transition-all duration-300 rounded-2xl border overflow-hidden hover:shadow-xl ${
      isInUse 
      ? 'bg-emerald-50/40 border-emerald-500 ring-4 ring-emerald-500/10' 
      : 'bg-white dark:bg-slate-800 border-slate-200 dark:border-slate-700 shadow-md'
    }`}>
      {isInUse && (
        <div className="absolute top-0 right-0 z-10">
          <div className="bg-emerald-600 text-white text-[10px] font-black px-4 py-1.5 rounded-bl-2xl flex items-center gap-2 shadow-lg uppercase tracking-widest">
            <CheckCircle2 size={14} />
            Em Uso
          </div>
        </div>
      )}

      <div className={`p-5 border-b ${isInUse ? 'bg-emerald-500/10 border-emerald-100' : 'bg-slate-50 dark:bg-slate-900/50 border-slate-200 dark:border-slate-700'}`}>
        <div className="flex justify-between items-start">
          <div className="flex-1">
            <div className="flex items-center gap-2 mb-2">
              <span className="bg-blue-600 text-white text-[10px] font-black px-2.5 py-1 rounded-md shadow-sm">{data.origin || 'JFK'}</span>
              <ArrowRight size={16} className="text-slate-400" />
              <span className="bg-emerald-600 text-white text-[10px] font-black px-2.5 py-1 rounded-md shadow-sm">{data.iata}</span>
            </div>
            <h3 className="font-black text-slate-800 dark:text-slate-100 text-xl leading-tight truncate pr-20">
              {data.name}
            </h3>
            <div className="flex flex-wrap gap-2 mt-2">
              <p className="text-slate-500 text-xs flex items-center gap-1 font-bold">
                <MapPin size={12} className="text-blue-500" /> {data.country}
              </p>
              <span className="bg-slate-200 dark:bg-slate-700 text-[10px] px-2 py-0.5 rounded font-black text-slate-600 dark:text-slate-300 uppercase">
                {data.aircraft || 'Aeronave'}
              </span>
            </div>
          </div>
          {!isInUse && (
            <div className="text-right">
              <div className="text-emerald-600 font-black text-2xl flex items-center justify-end">
                <span className="text-sm font-bold mt-1 mr-0.5">$</span>
                {(data.profit || 0).toLocaleString('en-US', { maximumFractionDigits: 0 })}
              </div>
              <p className="text-[10px] uppercase tracking-widest text-slate-400 font-black">Lucro / Voo</p>
            </div>
          )}
        </div>
      </div>

      <div className="p-5 space-y-5">
        <div className="grid grid-cols-3 gap-3">
          <div className="bg-slate-50 dark:bg-slate-900/50 p-2.5 rounded-xl text-center border border-slate-100 dark:border-slate-700">
            <p className="text-[9px] text-slate-400 uppercase font-black mb-1">Distância</p>
            <p className="text-sm font-black text-slate-700 dark:text-slate-200">
              {Math.round(data.dist || 0)} <span className="text-[10px]">km</span>
            </p>
          </div>
          <div className="bg-slate-50 dark:bg-slate-900/50 p-2.5 rounded-xl text-center border border-slate-100 dark:border-slate-700">
            <p className="text-[9px] text-slate-400 uppercase font-black mb-1">Duração</p>
            <p className="text-sm font-black text-slate-700 dark:text-slate-200 flex items-center justify-center gap-1">
              <Clock size={12} className="text-blue-500" /> {formatTime(data.time)}
            </p>
          </div>
          <div className="bg-slate-50 dark:bg-slate-900/50 p-2.5 rounded-xl text-center border border-slate-100 dark:border-slate-700">
            <p className="text-[9px] text-slate-400 uppercase font-black mb-1">Mercado</p>
            <p className="text-sm font-black text-slate-700 dark:text-slate-200">{data.market || 100}%</p>
          </div>
        </div>

        <div className={`p-4 rounded-xl border-2 transition-all ${
          isInUse 
          ? 'bg-emerald-600 text-white border-emerald-400 shadow-inner' 
          : 'bg-blue-50/30 dark:bg-blue-900/10 border-blue-100 dark:border-blue-900/20'
        }`}>
          <div className="flex justify-between items-center mb-3">
             <span className={`text-[10px] font-black uppercase tracking-wider ${isInUse ? 'text-emerald-100' : 'text-blue-600 dark:text-blue-400'}`}>
               Configuração e Valores
             </span>
             <Plane size={16} className={isInUse ? 'text-emerald-200' : 'text-blue-400'} />
          </div>
          <div className="grid grid-cols-1 gap-3">
            {[
              { label: 'Econômica (Y)', key: 'y', icon: '👤' },
              { label: 'Executiva (J)', key: 'j', icon: '👔' },
              { label: 'Primeira (F)', key: 'f', icon: '👑' }
            ].map(cls => (
              <div key={cls.key} className={`flex justify-between items-center pb-2 border-b last:border-0 ${isInUse ? 'border-emerald-500/50' : 'border-slate-200/50'}`}>
                <div className="flex items-center gap-2">
                  <span className="text-xs">{cls.icon}</span>
                  <span className={`text-xs font-bold ${isInUse ? 'text-emerald-50' : 'text-slate-600'}`}>{cls.label}</span>
                </div>
                <div className="text-right flex items-center gap-3">
                  <div className="flex flex-col items-end">
                    <span className="text-sm font-black leading-none">{data.config?.[cls.key] || 0}</span>
                  </div>
                  <div className={`px-2 py-1 rounded min-w-[60px] text-center ${isInUse ? 'bg-emerald-700' : 'bg-slate-200 dark:bg-slate-700'} font-black text-[11px]`}>
                    ${data.prices?.[cls.key] || 0}
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>

        <button 
          onClick={onToggleUse}
          className={`w-full py-3.5 rounded-xl text-xs font-black uppercase tracking-[0.2em] transition-all flex items-center justify-center gap-3 shadow-sm ${
            isInUse
            ? 'bg-slate-900 text-white hover:bg-black'
            : 'bg-white text-emerald-600 border-2 border-emerald-600 hover:bg-emerald-600 hover:text-white'
          }`}
        >
          {isInUse ? <><CheckCircle2 size={16} /> LIBERAR ROTA</> : <>UTILIZAR ROTA</>}
        </button>
      </div>
    </div>
  );
};

const App = () => {
  const [user, setUser] = useState(null);
  const [routes, setRoutes] = useState([]);
  const [inUseRoutes, setInUseRoutes] = useState({});
  const [loading, setLoading] = useState(true);
  
  // Filtros e Navegação
  const [searchTerm, setSearchTerm] = useState("");
  const [sortBy, setSortBy] = useState("profit");
  const [filterInUse, setFilterInUse] = useState("all");
  const [filterAircraft, setFilterAircraft] = useState("all");
  const [filterOrigin, setFilterOrigin] = useState("all");
  const [itemsPerPage, setItemsPerPage] = useState(100);
  const [currentPage, setCurrentPage] = useState(1);
  
  const fileInputRef = useRef(null);

  // 1. Iniciar Auth
  useEffect(() => {
    const initAuth = async () => {
      try {
        if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
          await signInWithCustomToken(auth, __initial_auth_token);
        } else {
          await signInAnonymously(auth);
        }
      } catch (err) {
        console.error("Erro auth:", err);
      }
    };
    initAuth();
    const unsubscribe = onAuthStateChanged(auth, setUser);
    return () => unsubscribe();
  }, []);

  // 2. Fetch Dados do Firestore
  useEffect(() => {
    if (!user) return;

    // Listen para rotas
    const routesRef = doc(db, 'artifacts', appId, 'users', user.uid, 'data', 'routes');
    const statusRef = doc(db, 'artifacts', appId, 'users', user.uid, 'data', 'status');

    const unsubRoutes = onSnapshot(routesRef, (docSnap) => {
      if (docSnap.exists()) {
        setRoutes(docSnap.data().list || []);
      }
      setLoading(false);
    }, (err) => console.error("Erro fetch routes:", err));

    const unsubStatus = onSnapshot(statusRef, (docSnap) => {
      if (docSnap.exists()) {
        setInUseRoutes(docSnap.data().active || {});
      }
    }, (err) => console.error("Erro fetch status:", err));

    return () => { unsubRoutes(); unsubStatus(); };
  }, [user]);

  const saveRoutesToCloud = async (newRoutes) => {
    if (!user) return;
    try {
      const routesRef = doc(db, 'artifacts', appId, 'users', user.uid, 'data', 'routes');
      await setDoc(routesRef, { list: newRoutes });
    } catch (err) {
      console.error("Erro save cloud:", err);
    }
  };

  const toggleRouteUse = async (id) => {
    if (!user) return;
    const newStatus = { ...inUseRoutes, [id]: !inUseRoutes[id] };
    setInUseRoutes(newStatus);
    try {
      const statusRef = doc(db, 'artifacts', appId, 'users', user.uid, 'data', 'status');
      await setDoc(statusRef, { active: newStatus });
    } catch (err) {
      console.error("Erro update status:", err);
    }
  };

  const handleFileUpload = (event) => {
    const file = event.target.files[0];
    if (!file) return;

    const fileName = file.name.toLowerCase();
    let detectedAircraft = "Aeronave";
    if (fileName.includes("mc214")) detectedAircraft = "MC-21-400";
    else if (fileName.includes("a320")) detectedAircraft = "A320";
    else if (fileName.includes("b737")) detectedAircraft = "B737";

    const reader = new FileReader();
    reader.onload = (e) => {
      const text = e.target.result;
      const lines = text.split('\n');
      if (lines.length < 2) return;

      const headers = lines[0].split(',').map(h => h.trim());
      const newRoutes = lines.slice(1).filter(l => l.trim()).map((line, idx) => {
        const values = line.split(',');
        const obj = {};
        headers.forEach((h, i) => { obj[h] = values[i]; });

        const uid = obj['dest.id'] || `${idx}-${Date.now()}`;
        return {
          id: uid,
          name: obj['dest.name'] || 'Destino',
          country: obj['dest.country'] || 'País',
          iata: obj['dest.iata'] || '???',
          dist: parseFloat(obj['direct_dist']) || 0,
          time: parseFloat(obj['time']) || 0,
          config: { y: obj['cfg.y'] || 0, j: obj['cfg.j'] || 0, f: obj['cfg.f'] || 0 },
          prices: { y: obj['tkt.y'] || 0, j: obj['tkt.j'] || 0, f: obj['tkt.f'] || 0 },
          profit: parseFloat(obj['profit_pt']) || 0,
          stopover: obj['stop.iata'] ? { iata: obj['stop.iata'], name: obj['stop.name'] } : null,
          market: Math.round(parseFloat(obj['market']) * 100) / 100 || 45,
          aircraft: detectedAircraft,
          origin: fileName.includes("jfk") ? "JFK" : "Origem"
        };
      });

      saveRoutesToCloud(newRoutes);
      setCurrentPage(1);
    };
    reader.readAsText(file);
  };

  const clearData = async () => {
    if(!user || !window.confirm("Isso apagará permanentemente suas rotas salvas. Continuar?")) return;
    try {
      const routesRef = doc(db, 'artifacts', appId, 'users', user.uid, 'data', 'routes');
      const statusRef = doc(db, 'artifacts', appId, 'users', user.uid, 'data', 'status');
      await deleteDoc(routesRef);
      await deleteDoc(statusRef);
      setRoutes([]);
      setInUseRoutes({});
    } catch (err) {
      console.error("Erro ao limpar:", err);
    }
  };

  const aircraftOptions = useMemo(() => ["all", ...new Set(routes.map(r => r.aircraft))], [routes]);
  const originOptions = useMemo(() => ["all", ...new Set(routes.map(r => r.origin))], [routes]);

  const allFilteredRoutes = useMemo(() => {
    let result = [...routes].filter(route => {
      const matchesSearch = route.name.toLowerCase().includes(searchTerm.toLowerCase()) || route.iata.toLowerCase().includes(searchTerm.toLowerCase());
      const isUsed = !!inUseRoutes[route.id];
      const matchesInUse = filterInUse === "all" ? true : filterInUse === "used" ? isUsed : !isUsed;
      const matchesAircraft = filterAircraft === "all" ? true : route.aircraft === filterAircraft;
      const matchesOrigin = filterOrigin === "all" ? true : route.origin === filterOrigin;
      return matchesSearch && matchesInUse && matchesAircraft && matchesOrigin;
    });

    result.sort((a, b) => {
      if (sortBy === "profit") return b.profit - a.profit;
      if (sortBy === "dist") return b.dist - a.dist;
      if (sortBy === "time") return b.time - a.time;
      return 0;
    });
    return result;
  }, [routes, searchTerm, sortBy, filterInUse, filterAircraft, filterOrigin, inUseRoutes]);

  // Lógica de Paginação
  const totalPages = Math.ceil(allFilteredRoutes.length / itemsPerPage);
  const paginatedRoutes = useMemo(() => {
    if (itemsPerPage === 0) return allFilteredRoutes; // "Ver Tudo"
    const start = (currentPage - 1) * itemsPerPage;
    return allFilteredRoutes.slice(start, start + itemsPerPage);
  }, [allFilteredRoutes, currentPage, itemsPerPage]);

  const stats = useMemo(() => {
    const inUseCount = Object.values(inUseRoutes).filter(v => v).length;
    const profit = allFilteredRoutes.reduce((acc, curr) => acc + curr.profit, 0);
    return { inUseCount, profit };
  }, [allFilteredRoutes, inUseRoutes]);

  if (loading && user) {
    return (
      <div className="min-h-screen flex items-center justify-center bg-slate-50 dark:bg-slate-950">
        <div className="text-center">
          <Loader2 className="animate-spin text-blue-600 mx-auto mb-4" size={48} />
          <p className="font-black text-slate-400 uppercase tracking-widest text-sm">Carregando Nuvem...</p>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-slate-50 dark:bg-slate-950 text-slate-900 dark:text-slate-100 p-4 md:p-8 font-sans">
      <div className="max-w-7xl mx-auto">
        
        {/* Header Profissional */}
        <header className="mb-8 flex flex-col lg:flex-row lg:items-center justify-between gap-6">
          <div className="flex items-center gap-4">
            <div className="bg-gradient-to-br from-blue-600 to-indigo-700 p-4 rounded-3xl shadow-xl">
               <MapIcon className="text-white" size={32} />
            </div>
            <div>
              <h1 className="text-3xl font-black tracking-tighter uppercase leading-none">
                AIRLINE <span className="text-blue-600">COMMANDER</span>
              </h1>
              <div className="flex items-center gap-3 mt-1">
                <p className="text-slate-500 text-[10px] font-black tracking-widest flex items-center gap-1 uppercase">
                  <Database size={10} className="text-blue-500" /> Sincronizado
                </p>
                <div className="h-3 w-px bg-slate-300 dark:bg-slate-700" />
                <p className="text-slate-500 text-[10px] font-black tracking-widest flex items-center gap-1 uppercase">
                  <User size={10} /> ID: {user?.uid.substring(0, 6)}...
                </p>
              </div>
            </div>
          </div>
          
          <div className="flex flex-wrap gap-3">
            <input type="file" accept=".csv" className="hidden" ref={fileInputRef} onChange={handleFileUpload} />
            <button 
              onClick={() => fileInputRef.current.click()}
              className="flex items-center gap-2 bg-blue-600 hover:bg-blue-700 text-white px-5 py-3 rounded-2xl font-black text-xs uppercase tracking-wider transition-all shadow-lg shadow-blue-500/20"
            >
              <Upload size={16} /> Carregar Novo CSV
            </button>
            
            {routes.length > 0 && (
              <button 
                onClick={clearData}
                className="p-3 rounded-2xl bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-red-500 hover:bg-red-50 transition-colors"
              >
                <Trash2 size={20} />
              </button>
            )}
          </div>
        </header>

        {/* Estatísticas Rápidas */}
        <div className="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
           <div className="bg-white dark:bg-slate-800 p-5 rounded-3xl shadow-sm border border-slate-200 dark:border-slate-700">
              <p className="text-[10px] uppercase font-black text-slate-400 mb-1">Rotas na Malha</p>
              <p className="text-3xl font-black text-slate-800 dark:text-white">{routes.length}</p>
           </div>
           <div className="bg-white dark:bg-slate-800 p-5 rounded-3xl shadow-sm border border-slate-200 dark:border-slate-700">
              <p className="text-[10px] uppercase font-black text-slate-400 mb-1">Ativas Agora</p>
              <p className="text-3xl font-black text-emerald-600">{stats.inUseCount}</p>
           </div>
           <div className="bg-white dark:bg-slate-800 p-5 rounded-3xl shadow-sm border border-slate-200 dark:border-slate-700">
              <p className="text-[10px] uppercase font-black text-slate-400 mb-1">Lucro Filtrado</p>
              <p className="text-3xl font-black text-blue-600">${stats.profit.toLocaleString('en-US', { maximumFractionDigits: 0 })}</p>
           </div>
        </div>

        {/* Filtros */}
        <div className="bg-white dark:bg-slate-800 p-6 rounded-3xl shadow-lg border border-slate-200 dark:border-slate-700 mb-8 space-y-6">
          <div className="relative">
            <Search className="absolute left-5 top-1/2 -translate-y-1/2 text-slate-400" size={24} />
            <input 
              type="text"
              placeholder="Pesquisar destino ou IATA..."
              className="w-full pl-14 pr-6 py-4 rounded-2xl bg-slate-50 dark:bg-slate-900 border-none focus:ring-4 focus:ring-blue-500/20 outline-none transition-all font-bold text-lg"
              value={searchTerm}
              onChange={(e) => {setSearchTerm(e.target.value); setCurrentPage(1);}}
            />
          </div>
          
          <div className="grid grid-cols-2 lg:grid-cols-5 gap-4">
            <div>
               <label className="text-[10px] font-black uppercase text-slate-400 ml-2 mb-2 block">Aeronave</label>
               <select className="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-900 border-none text-xs font-black uppercase" value={filterAircraft} onChange={(e) => {setFilterAircraft(e.target.value); setCurrentPage(1);}}>
                {aircraftOptions.map(opt => <option key={opt} value={opt}>{opt === "all" ? "Todas" : opt}</option>)}
              </select>
            </div>
            <div>
               <label className="text-[10px] font-black uppercase text-slate-400 ml-2 mb-2 block">Origem</label>
               <select className="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-900 border-none text-xs font-black uppercase" value={filterOrigin} onChange={(e) => {setFilterOrigin(e.target.value); setCurrentPage(1);}}>
                {originOptions.map(opt => <option key={opt} value={opt}>{opt === "all" ? "Todas" : opt}</option>)}
              </select>
            </div>
            <div>
               <label className="text-[10px] font-black uppercase text-slate-400 ml-2 mb-2 block">Status</label>
               <select className="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-900 border-none text-xs font-black uppercase" value={filterInUse} onChange={(e) => {setFilterInUse(e.target.value); setCurrentPage(1);}}>
                <option value="all">Ver Tudo</option>
                <option value="used">Em Uso</option>
                <option value="unused">Disponíveis</option>
              </select>
            </div>
            <div>
               <label className="text-[10px] font-black uppercase text-slate-400 ml-2 mb-2 block">Ordenar por</label>
               <select className="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-900 border-none text-xs font-black uppercase" value={sortBy} onChange={(e) => setSortBy(e.target.value)}>
                <option value="profit">Lucro</option>
                <option value="dist">Distância</option>
                <option value="time">Tempo</option>
              </select>
            </div>
            <div>
               <label className="text-[10px] font-black uppercase text-slate-400 ml-2 mb-2 block">Exibir</label>
               <select className="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-900 border-none text-xs font-black uppercase" value={itemsPerPage} onChange={(e) => {setItemsPerPage(parseInt(e.target.value)); setCurrentPage(1);}}>
                <option value={100}>100 por página</option>
                <option value={50}>50 por página</option>
                <option value={0}>Ver Todas</option>
              </select>
            </div>
          </div>
        </div>

        {/* Listagem */}
        {routes.length > 0 ? (
          <>
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-12">
              {paginatedRoutes.map((route) => (
                <RouteCard 
                  key={route.id} 
                  data={route} 
                  isInUse={!!inUseRoutes[route.id]}
                  onToggleUse={() => toggleRouteUse(route.id)}
                />
              ))}
            </div>

            {/* Paginação Controles */}
            {itemsPerPage > 0 && totalPages > 1 && (
              <div className="flex flex-col md:flex-row items-center justify-between gap-4 bg-white dark:bg-slate-800 p-6 rounded-[2.5rem] mb-12 shadow-sm border border-slate-200 dark:border-slate-700">
                <p className="text-xs font-black text-slate-400 uppercase tracking-widest">
                  Página {currentPage} de {totalPages} <span className="mx-2 text-slate-200">|</span> {allFilteredRoutes.length} rotas totais
                </p>
                <div className="flex items-center gap-2">
                  <button 
                    disabled={currentPage === 1}
                    onClick={() => setCurrentPage(p => p - 1)}
                    className="p-3 rounded-xl hover:bg-slate-100 dark:hover:bg-slate-700 disabled:opacity-30 disabled:cursor-not-allowed transition-colors"
                  >
                    <ChevronLeft size={20} />
                  </button>
                  
                  {/* Atalhos de páginas (simplificado) */}
                  <div className="flex gap-1">
                    {[...Array(Math.min(5, totalPages))].map((_, i) => {
                      let pageNum = i + 1;
                      if (currentPage > 3 && totalPages > 5) pageNum = currentPage - 3 + i + 1;
                      if (pageNum > totalPages) return null;
                      
                      return (
                        <button 
                          key={pageNum}
                          onClick={() => setCurrentPage(pageNum)}
                          className={`w-10 h-10 rounded-xl font-black text-xs transition-all ${currentPage === pageNum ? 'bg-blue-600 text-white shadow-lg' : 'hover:bg-slate-100 dark:hover:bg-slate-700 text-slate-500'}`}
                        >
                          {pageNum}
                        </button>
                      );
                    })}
                  </div>

                  <button 
                    disabled={currentPage === totalPages}
                    onClick={() => setCurrentPage(p => p + 1)}
                    className="p-3 rounded-xl hover:bg-slate-100 dark:hover:bg-slate-700 disabled:opacity-30 disabled:cursor-not-allowed transition-colors"
                  >
                    <ChevronRight size={20} />
                  </button>
                </div>
              </div>
            )}
          </>
        ) : (
          <div className="text-center py-32 bg-white dark:bg-slate-800 rounded-[3rem] border-4 border-dashed border-slate-100 dark:border-slate-800">
            <Upload size={48} className="mx-auto text-slate-300 mb-6" />
            <h3 className="text-2xl font-black text-slate-800 dark:text-slate-200 uppercase">Hub Desconectado</h3>
            <p className="text-slate-400 font-bold mt-2">Nenhum dado salvo em nuvem. Carregue seu CSV para começar.</p>
          </div>
        )}
      </div>
    </div>
  );
};

export default App;
